---
title: "Accessing d-link ntework from 8.04"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by squrl on 2009-12-19
I have a d-link DNS-321 network drive with two ata drives. According to d-link it won't work from linux. At least the man from India says it wont.

The url is 192.168.15.2  That much I learned. I can get to the front page for configuration but not to the drives.

Does anybody have any suggestions how to access volume_1 or volume _2

Thanks

---

### Post by squrl on 2009-12-19
bump

---

### Post by Iowan on 2009-12-20
Scanning through [this]("http://www.digitalhobbit.com/2008/11/26/hacking-the-d-link-dns-321-nas/") article, it appears the DNS-321 > makes two SATA drives available over Gigabit ethernet via SMB.  I presume it *should* look like a Windows share. [This]("http://ubuntuforums.org/showthread.php?t=1169149") How-To should help with some of the browsing problems.

---

