Hadoop Cluster
==============

Creates a Hadoop cluster including masters and workers. The cluster will use
Yarn as the scheduler.

Requirements
------------

This role requires that nodes have access to the internet. If this must be done
through a proxy, ensure the proxy settings are configured. This role has only
been tested with RHEL7 targets.

Role Variables
--------------

* `hadoop_vers`: Sets the upstream version to download and install. Defaults
  to "3.1.1".
* `hadoop_device`: The local drive to use for hdfs storage. Must be a block
  device, not a partition. Defaults to "/dev/sdb"
* `hadoop_replication`: Controls the amount of replication on the cluster.
  Defaults to "1".

Dependencies
------------

No other dependencies.

Example Playbook
----------------

```
- name: setup hadoop prerequisites
  hosts: hadoop

  roles:
    - hadoop-cluster
```

The `hadoop` group should contain three child groups:
* hdfs_masters
* hdfs_workers
* hdfs_clients

Nodes in the masters group will be the cluster master. Currently, only one host
should be placed in this group. Nodes in the workers group will be workers and
storage nodes. Nodes in the clients group will have hdfs installed and
configured, but will not be used for work or storage.


License
-------

Apache License 2.0

Author Information
------------------

Ryan Kraus
https://kraus.house
