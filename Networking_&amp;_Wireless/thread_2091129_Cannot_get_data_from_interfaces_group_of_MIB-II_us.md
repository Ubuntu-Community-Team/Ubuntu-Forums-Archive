---
title: "Cannot get data from interfaces group of MIB-II using snmp queries on Ubuntu"
date: 2012-12-04
forum: Networking &amp; Wireless
---

### Post by NBPX on 2012-12-04
Two machines running Ubuntu. One is running on Virtualbox inside the other.

Using the following command **in the VM** (get number of interfaces):

```
    snmpget -v 2c -c public localhost 1.3.6.1.2.1.2.1.0
```
I get the following result:


```
    iso.3.6.1.2.1.2.1.0 = INTEGER: 2

```
But, if I do it in the host (query to the VM):

```
    snmpget -v 2c -c public 10.1.14 1.3.6.1.2.1.2.1.0
```
I get:


```
    iso.3.6.1.2.1.2.1.0 = No Such Object available on this agent at this OID
```


I can do SNMP queries to objects of System Group, but cannot do SNMP queries to objects of Interfaces Group.


The machine is running Ubuntu 12.10 and the VM is running Ubuntu 12.04.

---

