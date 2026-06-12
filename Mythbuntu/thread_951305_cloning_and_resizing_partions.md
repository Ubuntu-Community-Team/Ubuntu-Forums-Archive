---
title: "cloning and resizing partions"
date: 2008-10-18
forum: Mythbuntu
---

### Post by mark467 on 2008-10-18
Ok I am somewhat new to linux but I thought I followed instructions fairly well. But, something went wrong. Setup as follows:

Hardware
Motherboard: Intel DG31PR
CPU: Intel® Celeron® Dual-Core processor E1200
RAM: 1 GB 667mhz DDR2
Video Card: PNY GeForce 8400gs PCIe
Sound Card: Intel® High Definition Audio 5.1 
HD: WD 500 GB SATA 2
DVD: Sony DRU-V200S/BR DVD/CD Rewritable Drive
OS: mythbuntu 8.041 (ubuntu myth combo)

I tried to upgrade my drive to a 1.5 TB seagate. I used clonezilla to clone the drive (i thought i had it set to resize the ext3 system part) but it made a duplicate of the size with about 1 tb unpartitioned. I then booted ubuntu live and used gparted to try and resize partition. It wouldnt let me resize the main part. so i removed the swap and then tried to resize it. it let me grow to about 1 tb then anything bigger it said cannot have a -1 sector or something (sorry i didnt write it down) and also recreated the swap at the end. It failed with other errors. Can ubuntu recognize drives bigger that 1 tb ? What can I be doing wrong. If more info is needed let me know. I would prefer to make the main part. full size (except about a 3gb swap) I am running mythbuntu and would find it easier than relocating folders.

---

### Post by DemonBob on 2008-10-18
Try the gparted live cd; it usually has a newer version then the ones in the ubuntu repo's 


[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Report back.

---

### Post by mark467 on 2008-10-18
I downloaded gparted with synaptic package manager. If you dont think that might be the most current I will try the gparted live cd.
Should what I am doing work?

---

### Post by DemonBob on 2008-10-18
Ext3 has a size limit of 8tb, so unless something is seriousaly wrong with the drive it should work fine.

---

