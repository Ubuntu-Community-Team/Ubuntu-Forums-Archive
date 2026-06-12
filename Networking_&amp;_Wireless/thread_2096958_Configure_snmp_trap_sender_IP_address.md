---
title: "Configure snmp trap sender IP address"
date: 2012-12-21
forum: Networking &amp; Wireless
---

### Post by DantePasquale on 2012-12-21
Hi we are running Ubuntu Server in a DMZ. It has 2 nics, ip address of public is 192.168.28.100 and ip address of private is 192.168.28.101. Hostname in /etc/hosts maps to the public IP address.

However, this is causing an issue regarding snmptraps being sent from this server as they originate using the public (28.100) address so the FW blocks them.

Is it possible, w/o changing the /etc/hosts, to configure the trap sending IP address to the private address, 28.101???

example with traps being sent to a Nagios monitoring station:

```
snmptrap -v1 -c public 192.168.8.128 .1.3.6.1.6.3.1.1.5.2 0 0 "" "" .1.3.6.1.4.1 s "hello
```"

Is blocked at FW.

---

