---
title: "Seeing other cmputers on home network"
date: 2009-10-19
forum: Networking &amp; Wireless
---

### Post by ras0556 on 2009-10-19
Good Morning... I would like to know how I go about seeing other computers on my home network.  We have a mix of OS's; 1 Vista laptop (ugh!), 2 running OS X (1, G4 & 1 macBook Pro) and two former XP PC's happily running Jaunty.  Is there a method of seeing all the computers in the workgroup or do I have to install a file server. I would like to be able to share audio files with all the PC's.  I realize with the mix of OS's that this probably won't be easy. But right now I can't even see the other devices.  Is there something in Ubuntu like Windows Network Neighborhood?

Thank You all in advance for the assistance.

---

### Post by Iowan on 2009-10-19
Peer-to-peer is a bit more involved. Every machine that will share (its own) files needs to have a server component installed.

---

### Post by calrogman on 2009-10-19
ping -c 4 -b 192.168.1.255

---

