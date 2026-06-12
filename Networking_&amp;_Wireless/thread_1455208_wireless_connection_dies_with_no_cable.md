---
title: "wireless connection dies with no cable"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by luthan on 2010-04-15
hello

i recently (through a lot of sweat and pain) installed the vt6656 wireless pci card that came with my zotac motherboard. 

i can associate with my ap and get an ip address successfully.  when i disconnect my ethernet cable, however, my wireless interface stops responding (can't ping it).  the box itself is in a place where i don't have a monitor connected to it so i cant see anything since my ssh session gets killed as soon as i disconnect the ethernet cable.

what would be the reason why the ehternet cable being unplugged, disconnects my wifi card as well?  does something get triggered?

i did some testing with iptables, blocking the 8080 traffic to the wired interface, and noticed that the 8080 traffic also gets blocked to the wifi ip.  i'm afraid that this never worked properly to begin with.

thanks for any help

---

### Post by NichoTL on 2010-04-27
On the top of my head I don't know what's wrong but why don't you start by setting up everything with a local login (ie plug in monitor, keyboard and mouse), and then remove the cable. To see if you still have the problem.

---

