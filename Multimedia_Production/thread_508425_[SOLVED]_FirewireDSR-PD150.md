---
title: "[SOLVED] Firewire/DSR-PD150"
date: 2007-07-24
forum: Multimedia Production
---

### Post by thebucksstop on 2007-07-24
Ok, so I've got a working FW800/400 PCMCIA card (2 9pin sockets, 1 6pin) on my laptop. It recognises my external hard drive through the 9pin socket, no problems.

The issue I have is trying to get the system to pick up my PD150 when I plug it in and turn it on. I want to digitise in some miniDV footage using Kino/dvgrab, but can't do that when I can't detect the camera. Can anyone walk me through this/help troubleshoot?

Thanks!

---

### Post by variona on 2007-07-24
AFAIK Kino wants raw1394 access (this is the only way to access your DV transport controls - OTH malware couldmake use of raw access. Either you add yourself to the group disk, or you change  
/etc/udev/rules.d/40-permissions.rules 
and change
KERNEL=="raw1394",			GROUP="disk"
to
KERNEL=="raw1394",			GROUP="INSERT_GROUP_YOU_BELONG_TO_AND_TRUST_HERE"

HTH

variona

---

### Post by thebucksstop on 2007-07-25
Thanks variona - that got it working :-)

Cheers!

---

