=================
Mesos integration
=================

**This software is pre-production and should not be deployed to production servers.**

.. contents:: Table of Contents

Mesos supported features
========================

- Monitoring
- Allocation

Mesos restrictions
==================

- Mesos version > 1.2.x,
- `Mesos containerizer <http://mesos.apache.org/documentation/latest/containerizers/#Mesos>`_,
- `Tasks groups <http://mesos.apache.org/documentation/latest/nested-container-and-task-group/>`_ are currently not supported.

Required agent options
------------------------------

- ``containerizers=mesos`` - to enable PID based cgroup discovery,
- ``isolation=cgroups/cpu,cgroups/perf_event`` - to enable CPU shares management and perf event monitoring,
- ``perf_events=cycles`` and ``perf_interval=360days`` - to enable perf event subsystem cgroup management without actual counter collection.

Following exact setup was verified to work with provided `workloads </workloads>`_:

- Mesos version == 1.2.6
- Docker registry V2
- Aurora framework version == 0.18.0

Mesos agent was configured with non-default options:

- ``perf_events=cycles``
- ``perf_interval=360days``
- ``isolation=filesystem/linux,docker/volume,docker/runtime,cgroups/cpu,cgroups/perf_event``
- ``cgroups_enable_cfs=true``
- ``hostname_lookup=false``
- ``image_providers=docker``
- ``attributes/own_ip=HOST_IP``