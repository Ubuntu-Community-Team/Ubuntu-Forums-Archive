---
title: "net-snmp-config"
date: 2006-06-21
forum: Networking &amp; Wireless
---

### Post by draven on 2006-06-21
A plugin I am trying to compile for Nagios requires the net-snmp-config binary. I can't find this any where. Google shows nothing, Ubuntuforums search shows nothing. What package offers this binary?

I currently have the following installed:
- libsnmp-base
- libsnmp5
- snmp
- tinysnmp-tools

---

### Post by draven on 2006-06-22
Nobody knows? I see it's built in the official net-snmp source, but does any Ubuntu package offer this as well?

---

### Post by isuraeru on 2007-03-15
You need to have installed libsnmpX-dev, where X is the snmp package version.

---

### Post by Peque on 2007-03-16
Hey Guys. 

I have an question. 
I have installed an Ubuntu dapper - and a Ubuntu edgy! I want to use along with Nagios to chech harddisk,CPU load , and RAM

it works allmost out off the box in Dapper, but installed the same packages ( from repos)  and copyed the Configurations files - but a netstat does not shows the machine is listening for SNMP. 
When I start/restarts the daemon - no errors

Have anybody and guess for this???

---

