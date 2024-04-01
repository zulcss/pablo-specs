---
title: D2O installer v1.0-experimental
---

# D2O Specification v1.0-experimental

**Note: This configuraiton is experiemtnal and has not been stablilized. It is
subject to change without warning or announcemnt.**

The D2O configuration is a YAML document conforming to the following
specification, with **_italicized_** entries being optional:

<div id="spec-docs"></div>

* ** name ** (string): used to differenate configs for different configuration
  types.
* ** description ** (string): used to describe what the purpose of the
  configuration file.
* ** version ** (string): the semantic version of the configuration.
* **_type_** (string): Shortened description of the installation type.
  Supported schemes are 'vanilla' and 'ostree'.
* ** architecture ** (string): The supported CPU architecture. Supported
  schemes are 'amd64' and 'arm64'.
* ** params ** (object):
   * ** disk ** (string): Disk deivce to install to.
   * ** _source_ ** (string): The rootfs tarball to install on to the disk. This
     applies to vanilla images.
   * ** _repository_ ** (string): The local ostree repository that contains the deployable branch. Starts with 'http'
   for a remote branch or a directory.
   * ** _branch_ ** (string): The ostree branch that is deployed to the disk.
* ** stages ** (object):
     * ** early ** (object): Tasks that take place before the installation
       begins.
          * ** _name_ ** (string): Description of the task to be performed.
          * ** _module_ ** (string): The module to execute, it is in a dotted
            notation.
          * ** _options_ ** (object): The arguments passed to the module.
     * ** disk ** (object): Tasks the operate on the disk deivce.
          * ** _name_ ** (string): Description of the task to be performed.
          * ** _module_ ** (string): The module to execute, it is in a dotted
            notation.
          * ** _options_ ** (object): The arguments passed to the module.
     * ** unpack ** (object): Tasks to unpack a rootfs tarball or create an ostree repo on to the disk.
          * ** _name_ ** (string): Description of the task to be performed.
          * ** _module_ ** (string): The module to execute, it is in a dotted
            notation.
          * ** _options_ ** (object): The arguments passed to the module.
     * ** install ** (object): Tasks to perform after the tarball or ostree
       branch has been deployed to the disk. 
          * ** _name_ ** (string): Description of the task to be performed.
          * ** _module_ ** (string): The module to execute, it is in a dotted
            notation.
          * ** _options_ ** (object): The arguments passed to the module.
    * ** post ** (object): Tasks to perform after intallation.
          * ** _name_ ** (string): Description of the task to be performed.
          * ** _module_ ** (string): The module to execute, it is in a dotted
            notation.
          * ** _options_ ** (object): The arguments passed to the module.

