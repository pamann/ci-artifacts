==============================
Node Feature Discover Operator
==============================

Deployment
==========

* Deploy the NFD operator from OperatorHub, and control the install
  channel

.. code-block:: shell

    toolbox/nfd/deploy_from_operatorhub.sh [nfd_channel, eg: 4.7]
    toolbox/nfd/undeploy_from_operatorhub.sh

Testing and Waiting
===================

* Test NFD deployment

(search for ``feature.node.kubernetes.io/system-os_release.ID=rhcos``
label)

.. code-block:: shell

    toolbox/nfd/has_nfd_labels.sh

* Test with NFD if NVIDIA GPU nodes are available

Search for these NVIDIA GPU PCI labels (that's the labels used by the `GPU Operator`_):

.. _GPU Operator: https://github.com/NVIDIA/gpu-operator/blob/bf20acd6717324cb4cf333ca9c8ffe8a33a70086/controllers/state_manager.go#L35

.. code-block:: shell

    feature.node.kubernetes.io/pci-10de.present
    feature.node.kubernetes.io/pci-0302_10de.present
    feature.node.kubernetes.io/pci-0300_10de.present

.. code-block:: shell

    toolbox/nfd/has_gpu_nodes.sh


* Wait with NFD for GPU nodes to become available

.. code-block:: shell

    toolbox/nfd/wait_gpu_nodes.sh
