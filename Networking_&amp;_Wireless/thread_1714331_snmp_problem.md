---
title: "snmp problem"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by tessio on 2011-03-25
In both CentOS 5.5 and FreeBSD 7.4 when I use 
```
snmpget -v 1 -c public windows_host system.sysDescr.0
```I get the remote windows machine system description just fine. But not in ubuntu.
Searching snmp-net FAQ for the erro message "Unknown Object Identifier", I got thist work around
```
snmpget -v 1 -c public 127.0.0.1 SNMPv2-MIB::system.sysDescr.0
```But it not worked either.. Searching "MIB" using apt-file search, I installed "snmp-mibs-downloader", and now
```
snmpget -v 1 -c public 127.0.0.1 SNMPv2-MIB::system.sysDescr.0
``` works.. but
```
snmpget -v 1 -c public windows_host system.sysDescr.0
``` still breaks..

Why it works in CentOS and FreeBSD but not in Ubuntu?

---

### Post by tessio on 2011-03-25
No one? :confused:

---

### Post by jos32 on 2011-09-02
> **tessio said:**
> 
```
snmpget -v 1 -c public 127.0.0.1 SNMPv2-MIB::system.sysDescr.0
``` works.. but
```
snmpget -v 1 -c public windows_host system.sysDescr.0
``` still breaks..

Why it works in CentOS and FreeBSD but not in Ubuntu?

AFAIK, You must use SNMP version 2c to get the sysDescr in Ubuntu.

---

