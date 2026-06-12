---
title: "kismet and linksys wusb54gc"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by dimas869 on 2008-12-31
i am using ubuntu hardy and i installed kismet from synaptic.
i checked the readme file...:D 
changed the suiduser and after some research about linksys wusb54gc i decided to use rt2400 source
when i try open kismet i get this message:

ramon@ramon-desktop:/etc/kismet$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
Source 0 (rt2400-gpl): Enabling monitor mode for rt2400 source interface eth0 channel 6...
FATAL: mode get ioctl failed 95:Operation not supported
Done.

could someone help me to properly configure?
thanks

---

### Post by dimas869 on 2009-01-01
thanks):P Allessio for helping me with the issue!!!!

---

