---
title: "network manager in intrepid"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by milou on 2009-01-01
Hello. Now under Intrepid, I noticed a change in network administration which I consider a regression, unless I missed something. Under Hardy, there was a "Network" entry in the menu " Administration" who allowed to fix in a graphical way the network system-wide, therefore in particular during the operating system start. Now, under Intrepid, the network is managed by an applet which is connected only after the login, so the machine is disconnected on gdm screen. Personally that is not appropriate to me because I mount NFS shares during the login with a script in /etc/gdm/PostLogin, and it is necessary for this that the machine is connected to my network wifi "BEFORE" login. I was thus forced to manually modify the /etc/network/interfaces file to fix my network " system wide". However in this case, Intrepid network manager does not function any more (this file has to be empty to work with the network manager). I do not understand why the Hardy graphical tool disappeared, it was more effective for managing system wide network settings. Or maybe I missed something , if someone could then explain me please :confused: …

---

