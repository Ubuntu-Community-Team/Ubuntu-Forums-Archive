---
title: "Networking a laptop and desktop"
date: 2012-03-04
forum: Networking &amp; Wireless
---

### Post by RemmyNumber7 on 2012-03-04
I am here again trying to find out some answers on how to network two computers together both running Linux Ubuntu 11.10.  I tried  Samba it didn't work and other Idea's or do I have to learn more about OSI and it's seven layers ????.  both are on-line by a single Ethernet cable. do I need a crossover cable in order to get the two machines to share files??????.

---

### Post by Iowan on 2012-03-05
> **RemmyNumber7 said:**
> both are on-line by a single Ethernet cable. do I need a crossover cable in order to get the two machines to share files??????.In the past, you'd need a crossover, hub/switch, or router to connect the two machines. Some modern cards (I don't have one) will auto-configure.
You'll also need to set up sharing - either NFS, SSH, Samba, etc. I haven't tried Personal File Sharing.

---

### Post by DrPotoroo on 2012-03-05
Modern network cards should not need a crossover cable. When you connect the two computers an LED should usually light up by the network socket on the computer if the connection is okay. Next you can run the command 'ifconfig' in a terminal on each machine to find out their IP addresses. When you are connecting two computers directly this way you most likely won't have a DHCP server assigning IP addresses, so you might need to set those up manually.

Once you confirm that each computer has a unique IP address (not the same as each other), try pinging one from the other. In a terminal:
```
ping xxx.xxx.xxx.xxx
```
Where xxx.xxx.xxx.xxx is the IP address for the other machine. Let it run a few seconds then press ctrl+c to stop the pinging. If you get packet losses reported you have a problem, if not you should be right to set up samba shares. Provided your networking is right, samba shares should pretty much just work.

---

