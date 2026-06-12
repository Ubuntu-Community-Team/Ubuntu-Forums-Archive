---
title: "Segate external media drive."
date: 2012-07-04
forum: Multimedia Software
---

### Post by MikeLitt on 2012-07-04
Ok Here is what I have. I own 2  segate 2tb xternal drive..  one is 100% great plug and play.  The other I plugged into my direct tv receiver to be used for more space. The receiver formatted the drive it worked for about 30 min. and has been a dead drive since.  Finally I need the space again and would like to be able to reformat it again.  it's been sitting dead for a yr. 

win box didn't see it lol didn't expect it to..  ubuntu box  didn't  I guess mount it..  but when I /terminal/lsusb I do see the drive in question..

 Bus 001 Device 024: ID 0bc2:5070 Seagate RSS LLC 

I am running the ubuntu that was current in feb of 2012 did not update it :) on a Dell latitude d820 if that helps..    

I really do need this my seed box is full and  new stuff i need to put in it :) 

Any help is greatly  welcomed.   I will also be without internet for next 4 days, Promptness is not a priority 

Ps I do fallow instructions well it you need more info just say so.

---

### Post by oldfred on 2012-07-04
Drives that have issues will often not be seen in gparted. Does gparted see it at all?

I had not issues ( I thought) with my sda drive, but then gparted would not see the drive at all. It had XP and XP still worked. I ran chkdsk on the NTFS partition and gparted saw it (and XP booted a bit faster).

Often external devices use FAT32. If it is that you should be able to run chkdsk on it also. But with 2TB it may take forever. I am not sure FAT works on drives that large and that may have been the issue.

---

### Post by MikeLitt on 2012-07-05
G parted is not seeing this drive.. :(  
The drive spins, it's stand by light comes on, I took it out of case and circuit board  looks to be 100% intact

I am figuring data on the drive to tell the pc what to do is corrupted

---

