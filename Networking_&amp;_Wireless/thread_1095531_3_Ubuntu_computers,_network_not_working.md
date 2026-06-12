---
title: "3 Ubuntu computers, network not working"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by gridsleep on 2009-03-13
Three computers each installed with Ubuntu 8.10.  My network is unusual.  I have a Xincom dual WAN router connected to two ISPs, one DSL, the other cable.  The three computers are a Toshiba laptop, a tower with an Asus motherboard and another tower with an iWill motherboard.  The three computers are connected to the Xincom router.  The Xincom router is connected to a D-Link wireless router by a patch cable, output port to output port.  DNS on the D-Link is disabled so it acts as a pass-through for the Xincom.  Connected to the D-Link is a wired network printer, and the laptop when I am using the wireless.  All three computers can browse the internet.  All three computers have access to the printer (which set up in about thirty seconds in Ubuntu, as opposed to ten minutes of futzing around in Windows.)  The three computers cannot see each other at all.  I have used gconf-editor to change the workgroup name so it matches on all three computers.  I don't even know why I need Samba since there are no Windows computers on this network.  (Well, the big tower has XP64 on dual boot, but only because Ubuntu can't access my television card, play my games, use Steam, or function with various pieces of exotic hardware.)  For file sharing, I only need the three Ubuntu platforms to access each other, and this they will not do.  When I was running Windows all around, the computers had no trouble sharing files.  What gives?  I also have the Public folder shared out on each computer.

---

### Post by gridsleep on 2009-03-16
I suppose if there is no answer then there is no solution.  I shall have to go back to using Windows, which is less inadequate than Linux.  I wish someone would come up with an operating system that actually works.  Or will we have to wait another three centuries for LCARS?  What a pathetic situation.

---

### Post by ugm6hr on 2009-03-16
> The three computers are connected to the Xincom router.

To be honest, I couldn't follow your network description, but I suspect this is all that is required.

Use either NFS or SMB:
[https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html](https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html)
[https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html](https://help.ubuntu.com/8.04/serverguide/C/configuring-samba.html)

Perhaps if you post a copy of the /etc/samba/smb.conf files you are using, that might help someone point you in the right direction.

---

