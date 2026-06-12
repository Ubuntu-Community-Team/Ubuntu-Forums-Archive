---
title: "XP Dual Boot Permissions"
date: 2012-01-06
forum: Mythbuntu
---

### Post by tmcgary on 2012-01-06
This is an odd question to be posing here but I am desperate. Here goes…


  I had a dual-boot mythbuntu/Win XP rig operating since 2008. It was running Mythbuntu 10.10. Due to WAF and other factors I am in the process of migrating to Windows 7 meda center alone.


  The dual boot setup involved the boot disc formatted as two partitions (+ swap), Ext4 for myth and NTFS for XP. Two additional internals media storage drives were formatted as NTFS (via XP disc management). The problematic drive, lets call it drive 1, had the majority of its media files transferred in windows, but was used for content rendering exclusively in mythbuntu and XBMC (in linux) using ntfs-config. At this time I noticed some permission problems with moving files into that drive in XP (“access denied”) but worked around it by using linux. 



  Now I am getting the same access denied in Windows 7 for the content on drive 1. Despite messing with every permission I can find in win7 management it does not seem to change the situation. This is a music library of 10,000 tracks, mostly copied from my own CDs so its hours and hours of work at stake.


  Has anyone encountered anything similar to this before? Is this a permissions issue from ubuntu? Is there a way to fix this from windows 7, either intrinsically or using some sort of virtual box to run a linux terminal and edit the files/folders permissions?


I am not opposed to reinstalling ubuntu to alter the permissions and then proceeding. I have never messed with permissions specifically, but have used the terminal a bit.



  Thank you for taking the time to read this. Any help is much appreciated!!!

---

### Post by tmcgary on 2012-01-09
I marked this as solved. I found a work-around. It turns out the problem dates back from the initial ripping of the CDs via dBpoweramp. So of the files were corrupted, and XP and Win7 wouldn't let me move them from the drive, hence the "access denied". However mythbuntu did and so everything was fine while I was using it. I don't fully understand the problem at all, but I have a solution.

---

