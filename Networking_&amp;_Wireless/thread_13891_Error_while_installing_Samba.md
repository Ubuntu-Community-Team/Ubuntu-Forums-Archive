---
title: "Error while installing Samba"
date: 2005-02-03
forum: Networking &amp; Wireless
---

### Post by Satyagraha on 2005-02-03
When I install samba, I get this error:

```
supersonic@supersonic:~ $ sudo apt-get install samba
Reading Package Lists... Done
Building Dependency Tree... Done
Suggested packages:
samba-doc
The following NEW packages will be installed:
samba
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B/2300kB of archives.
After unpacking 5984kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 103779 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.7-1ubuntu6.3_i386.deb) ...
Setting up samba (3.0.7-1ubuntu6.3) ...
[b]* Starting Samba daemons.. [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
samba
E: Sub-process /usr/bin/dpkg returned an error code (1)[/b]
supersonic@supersonic:~ $ 
``` 

What could posibly wrong?

---

