---
title: "network ethernet connection lost"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by eharx on 2009-11-05
Ubuntu 9.10
System is installed on an HP ZV6000. WLAN dead on arrival, as expected. Ethernet connection worked immediately, and still works from booted install CD.  User inadvertently installed and ran 2 utilities (WIFI Radar and Kwlan) in an attempt to get the wlan connected, without the broadcom driver being installed. The ethernet connection is now dead. The network manager icon is missing from the panel, although it's in the list of startup selections, and there on CD booted system. Possibly irrelevant, but bodes ill. lshw reports that the ethernet hw is DISABLED. 
When I open /etc/network/interfaces I see the lines:
  auto lo
  iface lo inet loopback
which is clearly not right, but it is impossible to edit this file, nor can I find info as to how I get 100% control of MY pc, ie global logon as owner / superuser.
Unfortunately the billions of obsolete and guru-jargonised links on the web make solution seeking there impossible.
Ubuntu is pretty attractive, and I will be a bit sad to go back to XP, but if I have to reinstall a system from scratch to get back on the web on that pc, it will be from an XP disc.
Any concrete tips also with appropriate info as to how to edit flop.init or whatever would be much appreciated.

---

### Post by Iowan on 2009-11-05
> **eharx said:**
> When I open /etc/network/interfaces I see the lines:
  auto lo
  iface lo inet loopback
which is clearly not right, That's pretty normal for a Network Manager controlled machine.

> **eharx said:**
> but it is impossible to edit this file,You tried it with ```
sudo nano /etc/network/interfaces
``` or ```
gksudo gedit /etc/network/interfaces
```

---

### Post by eharx on 2009-11-06
Solved, thanks Iowan!   ):P

---

