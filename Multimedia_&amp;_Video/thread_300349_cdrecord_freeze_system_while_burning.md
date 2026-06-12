---
title: "cdrecord freeze system while burning"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by sssilent on 2006-11-15
I'm after upgrade from Dapper to Edgy. But I have big problem with burning CDs. 

When cdrecord starts to burn CD, my system is freezing, I can't move cursor, type something - I can only press RESET button.

I have this problem in every burning applications (k3b, graveman, gnomebaker). I know, that the source of this problem is cdrecord.

I tried many solutions, but I still can't solve this problem. 

I'm desperated, I don't know what to do. Please, help me, I don't want to change system...

---

### Post by bigcnz on 2006-11-19
I am having the exact same problem. I've tried burning different iso's with different programmes all of which freeze the system completely (the computer must be restarted). Any ideas?

Ubuntu 6.10

dmesg | grep -i cd | grep -i rom:
  [17179575.848000] hdd: ATAPI CD-RW 52XMax, ATAPI CD/DVD-ROM drive
  [17179576.060000] hdd: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
  [17179576.060000] Uniform CD-ROM driver Revision: 3.20
  [17179602.072000] cdrom: hdd: mrw address space DMA selected
  [17179624.772000] cdrom: This disc doesn't have any tracks I recognize!


fstab:
  /dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by nozyczek on 2007-01-16
Hey guys. 
Did you solve it because I have the same problem. 
Thanks for any help
nozyczek

---

### Post by nibsa1242 on 2007-02-02
I have this problem when I don't run cdrecord as root. Even as root I still make coasters.

---

