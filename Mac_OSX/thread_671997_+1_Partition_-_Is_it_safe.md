---
title: "+1 Partition - Is it safe?"
date: 2008-01-19
forum: Mac OSX
---

### Post by Ballena on 2008-01-19
Hi there



I have , after many hours of hard work, managed to install both Windows XP and Ubuntu on my iMac( by following this [this](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp) guide) and I have rEFIt as my boot manager.I have one harddrive which is 750G and it's partition looks like this:

Macintosh:~ ballena$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE         IDENTIFIER
   0:       GUID_partition_scheme                  *698.6 Gi   disk0
   1:       EFI                                                200.0 Mi    disk0s1
   2:       Apple_HFS Macintosh HD                 599.9 Gi    disk0s2
   3:       Microsoft Basic Data                        27.9 Gi     disk0s3
   4:       Microsoft Basic Data Windows           70.4 Gi     disk0s4

As you can see I have two partition but I want one **more** jHFS+ partition where I can save all my personal files. But I have heard that you only can have 4 partition on the same HDD. Is that true? Will Windows or ubuntu stop working if I resixe my Apple_HFS_Macintosh_HD partition and make another one? Because Windows stop working once when I added a new partition - but this was when I installed Windows with Boot Camp only and made the partition with the BC-tool. which I haven't now.

So dare I make another partition from mac Mac-partition or not? I appreciate any help I can get with this.
/Ballena

---

### Post by Infinite Recursion on 2008-03-23
I haven't tried this myself, but from what I understand adding a fifth partition will cause some problems with Windows.  It seems that if you have more than 4 partitions, it will simply kick the last one off of the MBR (required to boot into Windows--the four-partition restriction doesn't seem to apply to GPT). 

If the last partition is Windows (if you insert a new partition in the middle, as you indicated that you would), then Windows will no longer be reflected on the MBR mirror, and will therefore be unusable.  If the last partition is something else, then Windows won't boot because of the restriction that it has to be on the last partition on the drive.

(It would make sense to me that since Windows would still be on the last partition in the *MBR* mirror, while not necessarily the GPT, the latter configuration might still work - can anyone confirm one way or another?)

Either way, while I doubt it would have any adverse effects on Mac OS X or Ubuntu, Windows will probably be unbootable.

Edit: As Cyberdork33 indicated in response to a previous post of mine ([http://ubuntuforums.org/showthread.php?t=724936](http://ubuntuforums.org/showthread.php?t=724936)), the only restriction is that Windows has to be in the final MBR partition.  Anything after that shouldn't affect it.  As such, you should be able to add a partition to the end of your scheme, though that could prove to be somewhat more difficult.

---

