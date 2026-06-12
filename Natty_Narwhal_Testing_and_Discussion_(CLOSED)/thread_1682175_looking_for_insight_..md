---
title: "looking for insight ."
date: 2011-02-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ronacc on 2011-02-05
I'm not sure what to think , since starting natty testing at repo open I have had 4 hard drives in my test box come up showing bad superblocks . various attempts to recover them have not helped and I can't get a good install to those drives ( I have also tried to install sabayon , suse and maverick to those drives no help ? now the strange thing is that if I remove the drives and put them in another box they are ok and If I install a system on them they work ok but not in my test box ? they are differnt interfaces makes and sizes so I have a hard time thinking that I have lost both 1 ide and 1 sata controler on my MB .any thoughts on this are welcome .

---

### Post by dino99 on 2011-02-05
i get some "blocks in the future" each time i boot since 2 days or so, but they are automatically fixed by the system boot.

---

### Post by ronacc on 2011-02-05
this started for me with alpha 1 ,  I had upgraded a fresh maverick install at repo open and was going to try to install A1 to a different drive  , that drive came up with a bad superblock on first boot of A1 , same story a few days later with a daily to still a different drive and a few days later with another try at A1 and this AM my upgraded maverick did the same thing on reboot after an update . Thats when I wrote the OP . attempts to repair the drives with fsck fail even with alternate SB;s .

---

### Post by cariboo on 2011-02-05
To me that looks like an indication that the motherboard is starting to fail. I had one a few years back that was doing something similar, first fake raid had problems with data corruption, breaking the array apart help for a whiled, but then the boot drive, pata, started suffering from data corruption, eventually the system just died.

---

### Post by plun on 2011-02-05
> **ronacc said:**
> this started for me with alpha 1 ,  I had upgraded a fresh maverick install at repo open and was going to try to install A1 to a different drive  , that drive came up with a bad superblock on first boot of A1 , same story a few days later with a daily to still a different drive and a few days later with another try at A1 and this AM my upgraded maverick did the same thing on reboot after an update . Thats when I wrote the OP . attempts to repair the drives with fsck fail even with alternate SB;s .

Well... during the EXT4 introducing my system totally collapsed....disk and memory errors everywhere.... it ended with a new MB.... "chriscoulson" checked my bug reports but it was a complete mess.

With my latest laptop I have my install since June last year....Maverick and Natty..... without any real trouble. !

---

### Post by MacUntu on 2011-02-05
Just look at the output of

```
sudo apt-get install smartmontools
sudo smartctl -A /dev/sda
```

Reallocated_Sector_Ct, Reallocated_Event_Count, Current_Pending_Sector, Offline_Uncorrectable ideally should be zero. If not, let the manufacturer tool map out bad sectors and if you still see problems, replace the drives.

---

### Post by ronacc on 2011-02-05
I  haven't had any problems with ext4 until now , all of the problems have occurred immediately after trying to install natty to the drives , the last one I mentioned , my upgrade from maverick doesn't seem to be the same thing , I can chroot in from a live cd and update etc but can't even boot to a recovery console , the boot stops right after init -scripts bottom and disconnecting from plymouth I've tried changing my xorg.conf a couple of times no help . 

@ cariboo907  could be an MB going flaky I'm going to try a few more things before I give up on it though,I think there is a small possibility that it has something to do with the way natty is ordering the drives , even the live cd doesn't call the same drive the same thing on 2 successive boots ( I really have to be carefull where I chroot to ).

---

