---
title: "Accessing USB HD using Belkin N+ (F6D6230uk4)"
date: 2012-12-19
forum: Networking &amp; Wireless
---

### Post by Spiddekaga on 2012-12-19
Hi!

I've got a laptop with Ubuntu 12.10 using a Belkin N+ router (F6D6230uk4) for wifi. Attached to the router is a USB HDD acting as a NAS in my network, but I can't access it!

Running Windows I can access the disk using the IP-adress (192.168.2.1) and the Username (guest) and Password(<empty>), but given the same parameters it just won't work in Ubuntu.
Found another thread in this forum regarding another Belkin N+ router that have helped many others, but using the information just won't do it for me!

When I map the disk(s) in Nautilus usning: smb://192.168.2.1/ I can see the two partitions on the disk as "sda1" and "sda2". When i click either of them I have to write username, workgroup and password. As suggested in the thread I read you set username to "guest", workgroup to "Belkin" and password as <empty>, but i don't get access anyway. I have checked the router to be sure "Belkin" is the "Local Domain Name..". Also tried "Mount Server" but the result is the same!

Does anyone know how to work around this??

---

### Post by Spiddekaga on 2013-01-01
No one know how to solve this?

---

### Post by BlinkinCat on 2013-01-01
> **Spiddekaga said:**
> No one know hos go solve this?

I would suggest you may bump the thread each 24 hours rather than waiting a week - :)

---

### Post by gordintoronto on 2013-01-01
Run the file manager, select Browse Network. Drill down to the drive.

---

### Post by Spiddekaga on 2013-01-04
> **gordintoronto said:**
> Run the file manager, select Browse Network. Drill down to the drive.

I can see the disks mounted via the wifi-router as "sdb1" and "sdb2". Trying to access them results in a dialog window asking for username, domain and password. When accessing disk in Windows I put "guest" as username and password is left empty, domain is Workgroup in Windows, domain set by router is Belkin, neither of these two work. Seems like I'm stuck :(

---

### Post by gordintoronto on 2013-01-04
The domain is probably workgroup, all lower case. In Linux, case is a big deal.

---

### Post by Spiddekaga on 2013-01-11
Bump

Getting really annoyed by this problem. Everything else runs so smooth in Ubuntu, but accessing my "NAS" is just impossible. 
Could I access it any other way than as a Windows network??

---

