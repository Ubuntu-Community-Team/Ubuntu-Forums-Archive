---
title: "No permission on my mobile phone"
date: 2012-10-29
forum: Mobile Technology Discussions (CLOSED)
---

### Post by loopinaloop on 2012-10-29
Hi there!
I have a mobile phone and I've never experienced any major issues with it. Now, it's a disaster for me. After making a fresh install of Ubuntu 12.10 I cannot make any changes on my mobile device. I get an error message that I've no permission. What I've changed is that I've made something around 7 partitions - maybe that's the cause? I've tried to install fresh Ubuntu 12.04 but that didn't helped so I revered back to 12.10.

As always, all problems began with an update... ;)

---

### Post by Ms. Daisy on 2012-10-29
What method did you use to install Ubuntu on the phone? What kind of phone? 

How did you manage to create 7 partitions? I'm assuming some of those are logical partitions? Can you show us the output from gparted?

---

### Post by wildmanne39 on 2012-10-30
*Thread moved to **Mobile Technology Discussions**.*

---

### Post by Mark Phelps on 2012-10-30
Are you saying: 
1) You installed 12.10 to your mobile phone -- which has seven partitions on it -- and now you can't do anything on the phone?
2) You installed 12.10 to your desktop -- which has seven partitions on it -- and now you can't access the phone from your desktop?

Very different questions -- very different problems.

---

### Post by loopinaloop on 2012-10-30
> **Mark Phelps said:**
> 2) You installed 12.10 to your desktop -- which has seven partitions on it -- and now you can't access the phone from your desktop?
I've installed Ubuntu on my desktop computer and I have read-only permission on my mobile.

---

### Post by Rexilion on 2012-10-31
What phone is it? How do you access it? (USB, bluetooth). Does it show up as a 'mass storage' device or is it an MTP device?

Connect the phone, access it's data and post the output of:

> sudo dmesg | tail -n20

---

### Post by loopinaloop on 2012-11-13
> **Rexilion said:**
> What phone is it? How do you access it? (USB, bluetooth). Does it show up as a 'mass storage' device or is it an MTP device? Connect the phone, access it's data and post the output of:

 I'm using Nokia XpressMusic via USB cable and it seems to be shown as 'mass storage' but I'm not sure (I'm using Polish language). I get following data after using your command: 

[12466.510238] usb 3-3: SerialNumber: 354196027580271
[12466.512553] scsi3 : usb-storage 3-3:1.0
[12467.516557] scsi 3:0:0:0: Direct-Access     Nokia    Nokia 5310 Xpres 0000 PQ: 0 ANSI: 4
[12467.518816] sd 3:0:0:0: Attached scsi generic sg2 type 0
[12467.529460] sd 3:0:0:0: [sdb] Adjusting the sector count from its reported value: 3907585
[12467.529477] sd 3:0:0:0: [sdb] 3907584 512-byte logical blocks: (2.00 GB/1.86 GiB)
[12467.535505] sd 3:0:0:0: [sdb] Write Protect is off
[12467.535520] sd 3:0:0:0: [sdb] Mode Sense: 04 00 00 00
[12467.541497] sd 3:0:0:0: [sdb] No Caching mode page present
[12467.541510] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[12467.565457] sd 3:0:0:0: [sdb] Adjusting the sector count from its reported value: 3907585
[12467.577438] sd 3:0:0:0: [sdb] No Caching mode page present
[12467.577451] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[12467.586434]  sdb: sdb1
[12467.600331] sd 3:0:0:0: [sdb] Adjusting the sector count from its reported value: 3907585
[12467.620297] sd 3:0:0:0: [sdb] No Caching mode page present
[12467.620311] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[12467.620318] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[12470.440355] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
[12470.440366] FAT-fs (sdb1): Filesystem has been set read-only

---

### Post by Rexilion on 2012-11-13
> **loopinaloop said:**
> [12470.440355] FAT-fs (sdb1): error, fat_get_cluster: invalid cluster chain (i_pos 0)
[12470.440366] FAT-fs (sdb1): Filesystem has been set read-only

There is your cause and explanation.

Seems like the filesystem is corrupt, or (which is always possible with Linux) the driver handling the filesystem is not capable of dealing with 'something there'.

I suggest you back-up your data and reformat it. Or alternatively, plug it in Windows and run a disk check (or even check that it works).

**After some googling I find a more [in depth explanation here]("http://serverfault.com/questions/331779/how-do-i-debug-this-fs-error-on-a-flash-device") and a [better way to workaround it]("http://www.delodder.be/blog/linux/fat_get_cluster-invalid-cluster-chain-i_pos-0-fat-filesystem-panic-dev/") (instead of a full reformat). Furthermore, [this page says it's because of an unclean disconnect.]("https://help.ubuntu.com/community/Mount/USB")**

---

### Post by loopinaloop on 2012-11-13
Superb!
I see no problem with formatting my device. Can you drop a line or two? I'm reading those links now but I'm not sure which solution would be best. If there is one, simple method (like formatting my memory card) then I would stick to it.

Thanks a lot! With people like you Linux is no longer intimidating nor difficult. An excellent support that you provide is an antidote to any frustration that can arise while using this system without advanced computer skills. I appreciate your time. Again, thank you!

---

### Post by loopinaloop on 2012-11-13
sudo fsck.msdos -aw /dev/sdb1

This command worked! Thanks again!

---

