---
title: "Samba ISO sharing"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by broomyocymru on 2008-12-31
I'm a bit of a newbie to Samba but here goes...

I have file sharing set up successfully on my wireless network and now want to share ISO files as mounted discs, ie pretend theres a disc on the network somewhere.

Using gmount-iso I've managed to share the iso mount to windows. The problem is its showing in windows as a directory (even after changing smb.conf to share file like a cd drive).

My question is can I share it tricking windows to believe the mount is hardware or is samba the wrong tool for this??

---

### Post by oygle on 2008-12-31
What about in Windows, map the network share to a 'drive' ?

---

