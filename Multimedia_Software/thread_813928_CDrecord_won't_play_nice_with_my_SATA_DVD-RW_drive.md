---
title: "CDrecord won't play nice with my SATA DVD-RW drive"
date: 2008-05-31
forum: Multimedia Software
---

### Post by tghe-retford on 2008-05-31
I can't get CDRecord to work on my computer, no matter what I do, it doesn't want to play nice with my SATA DVD-RW. I have to use CDrecord as per the instructions in this post: [http://ubuntuforums.org/showpost.php?p=4855862&postcount=10](http://ubuntuforums.org/showpost.php?p=4855862&postcount=10) (not too keen on having to fork out cash if there is a program(s) which can do it for free). Although CDIrip worked perfect and left me with a .wav and .iso file ready for CDrecord to burn, CDrecord won't play nice and spits out this error when I try the CDrecord instructions from the link in the aforementioned post, with this command:
```
cdrecord dev=2,0,0 speed=4 -v -multi -audio taudio01.wav
```
```
Script started on Sat 31 May 2008 13:41:21 BST
]0;sonic@tghe: ~/Desktop/cdripsonic@tghe:~/Desktop/cdrip$ script test.logcdrecord dev=2,0,0 speed=8 -v -multi -audio taudio01.
.wav[A[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C ~/Desktop/cdrip[K


[K[A[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[C[Crecord dev=2,0,0 speed=4 -v -multi -audio taudio01.
.wav

wodim: No write mode specified.

wodim: Asuming -tao mode.

wodim: Future versions of wodim may have different drive dependent defaults.

TOC Type: 0 = CD-DA

wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '2,0,0'

scsibus: 2 target: 0 lun: 0

WARNING: the deprecated pseudo SCSI syntax found as device specification.

Support for that may cease in the future versions of wodim. For now,

the device will be mapped to a block device file where possible.

Run "wodim --devices" for details.

Unable to open this SCSI ID. Trying to map to old ATA syntax.This workaround will disappear in the near future. Fix your configuration...
(this bit carries on forever and forever until you close the terminal)
```
Apologies for the odd characters. The only way I could get the output was through running a script.

The output of wodim --devices:
```
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'	rwrw-- : 'SONY' 'DVD RW DRU-190S'
-------------------------------------------------------------------------
```
And the output of wodim -scanbus
```
scsibus2:
	2,0,0	200) 'SONY    ' 'DVD RW DRU-190S ' '1.62' Removable CD-ROM
	2,1,0	201) *
	2,2,0	202) *
	2,3,0	203) *
	2,4,0	204) *
	2,5,0	205) *
	2,6,0	206) *
	2,7,0	207) *
```
I am absolutely puzzled as to what to do next. It asks me to fix my configuration but I don't know where to go from here. I can't use the trial version of Alcohol 120% in Wine for the image I am trying to burn, although the image burns without error, it fails to work on my Dreamcast, though it works perfect on lxDream. I suspect CDrecord will not work with my SATA DVD-RW.

Any thoughts would be welcome. Thanks in advance.

---

### Post by tghe-retford on 2008-05-31
I have tried trial versions of Alcohol 120% (which worked on my old computer using Ubuntu) and Discjuggler using Wine, and all that happens is coaster after coaster. Tried all sorts of options and tutorials I could find on Google. No joy. Tried cdi2nero using Wine and burning it using Alcohol 120%. That didn't work and created another coaster. Bootdreams - nada.

My burner does work because I burned an ISO image using K3B earlier tonight and it worked first time without problems.

But because of the way the Dreamcast reads discs, cdi2iso will never work.

I've wasted 11 CD-R discs trying to figure this problem out and other options. :( Anyone?

---

