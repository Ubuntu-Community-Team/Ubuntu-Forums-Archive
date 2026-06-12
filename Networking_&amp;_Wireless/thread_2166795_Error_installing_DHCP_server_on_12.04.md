---
title: "Error installing DHCP server on 12.04"
date: 2013-08-11
forum: Networking &amp; Wireless
---

### Post by mattyhatty on 2013-08-11
Any help?I get the following error installing isc-dhcp-server:

```
sudo apt-get install isc-dhcp-server
[sudo] password for dan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  isc-dhcp-server-ldap
The following NEW packages will be installed:
  isc-dhcp-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/428 kB of archives.
After this operation, 1,040 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package isc-dhcp-server.
(Reading database ... 255302 files and directories currently installed.)
Unpacking isc-dhcp-server (from .../isc-dhcp-server_4.1.ESV-R4-0ubuntu5.8_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up isc-dhcp-server (4.1.ESV-R4-0ubuntu5.8) ...
Generating /etc/default/isc-dhcp-server...
start: Job failed to start
invoke-rc.d: initscript isc-dhcp-server, action "start" failed.
dpkg: error processing isc-dhcp-server (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 isc-dhcp-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by gordintoronto on 2013-08-11
It looks like it was already installed.

---

