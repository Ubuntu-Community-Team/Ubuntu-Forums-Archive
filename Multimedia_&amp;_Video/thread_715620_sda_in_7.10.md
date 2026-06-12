---
title: "sda in 7.10"
date: 2008-03-05
forum: Multimedia &amp; Video
---

### Post by robert shearer on 2008-03-05
On an old P3 Feisty was upgraded to Gutsy and it retained the sda1 sda2 etc labels for partitions (why ?). It has performed well and I can burn cds dvds and rw media with ease.I have tried a number of burning applications and all work ok.

Recently I installed Gutsy on an old Celeron equivalent of the P3 but the hard drive icons report as hda1 hda2 etc and the disk drives as hdc and hdd.On this machine only Nautalis will burn disks and any other burning app I try either fails to find my burner or misreports the media( I especially like the blank cd-r that Brasero says has 171,000,000,000 GB of data and is therefore unwriteable - if only!.)

Needless to say the burners work fine in win2K on the same machine.
I tried installing Gutsy from the live cd and the alternate install cd but still no sda et al.

I was resigned to thinking it was related to hardware and unable to be changed but then installed Mepis 7 on the same machine and hard-drive alongside Gutsy and win2K.
Mepis installed and reports the drive as sda and my burner as scd0, my dvdplayer  as scd1 and I can burn cds and cdrw fine with k3b.(k3b in Gutsy was a failure too).

How can I get Gutsy to do the same ?.Don't Mepis7 and Gutsy share  the same Debian source ? Why does one install of Gutsy use sda and the other hda and can I change this ?.

---

### Post by itix on 2008-03-05
I can't help you with the burning software, but I CAN tell you that it has nothing at all with the hard drives to do. I may depend on what label the burners are, and how well developed drivers they have for linux. Lexmark printers for example can't be used by linux machines since Lexmark refuse to create restricted drivers or give out any details on the structure wich is required to write a driver.

Your burner might have the same issue. I don't know which works and which don't so that would be someone elses department.

Personally I use k3b (with normal 0.7 Gb discs :) ) and I love the silly fanfare in the end of each burning...

---

