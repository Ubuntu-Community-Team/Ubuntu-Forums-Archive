---
title: "Fiesty screwed everything up, Ipod"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by bestial on 2007-05-13
So, I finally upgrade to fiesty in the belief that everything where gonna be so smooth. I have'nt hade anything else then trubble since I did. The most recent thing is that my ipod doesn't show up in neither nautilus, thunar or in banshee. This is driving me crazy. I have tried, sudo mount /dev/sdb2 /media/ipod, which worked in it's own kinda way, the ipod shows up in /media but not in banshee nor amarok.

So, anyone have any solution to this? It's kinda bizarre that something that used to work in the earlier versions of ubuntu suddenly doesn't.

But as always, it works for some, and don't for others, I guess.

---

### Post by Swankyman on 2007-05-13
hi

after you plug your ipod in what the last few lines of the dmesg command say??

rich

---

### Post by bestial on 2007-05-13
[74253.185112] scsi 8:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[74253.201434] sdb: Spinning up disk........ready
[74258.297186] SCSI device sdb: 7999487 512-byte hdwr sectors (4096 MB)
[74258.298056] sdb: Write Protect is off
[74258.298064] sdb: Mode Sense: 64 00 00 08
[74258.298068] sdb: assuming drive cache: write through
[74258.300115] SCSI device sdb: 7999487 512-byte hdwr sectors (4096 MB)
[74258.301549] sdb: Write Protect is off
[74258.301555] sdb: Mode Sense: 64 00 00 08
[74258.301558] sdb: assuming drive cache: write through
[74258.301563]  sdb: sdb1 sdb2
[74258.364751] sd 8:0:0:0: Attached scsi removable disk sdb
[74258.364816] sd 8:0:0:0: Attached scsi generic sg2 type 0

---

