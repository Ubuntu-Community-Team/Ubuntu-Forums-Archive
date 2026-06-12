---
title: "Ubuntu 6.06, samba time offset"
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by craigiebabe on 2006-07-15
Anybody here experiencing issues with the "time offset" parameter in smb.conf??

My installation seems to be ignoring anything I place into time offset. 60, +60, +120, etc.

Not sure if this is a bug with the version of samba in ubuntu 6.06, ubuntu 5 (and previous) worked perfectly. Testparm acknowledges the parameter but restarting the daemon does nothing.

Bizarre...

craig@pluto:/etc$ testparm --version
Version 3.0.22

Any offers? :(

---

### Post by craigiebabe on 2006-07-15
Well in the meantime I've rolled back to...

smbclient_3.0.14a-6ubuntu1.1_i386
samba-common_3.0.14a-6ubuntu1.1_i386
samba_3.0.14a-6ubuntu1.1_i386

Works perfectly. I guess I'll wait till someone compiles and packages 3.0.23 and see if the problem goes away!

---

