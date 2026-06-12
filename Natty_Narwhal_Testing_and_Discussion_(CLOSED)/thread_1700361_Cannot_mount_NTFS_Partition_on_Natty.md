---
title: "Cannot mount NTFS Partition on Natty"
date: 2011-03-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by PRGUY85 on 2011-03-04
Don't know if this is the place to post this but I have a secondary "media" internal hard drive with a single NTFS partition that I just cannot mount in Natty. I haven't been able to do so on any iteration of this build.  It doesn't show up on my Devices. On GParted2 it just says unallocated space 500GB, no partition whatsoever.  However, in previous versions of Ubuntu I could definitely use the device. On Windows 7 (dual boot), the device is mounted as expected and functional.  I did a clean up of the drive of Win7 and cleaned bad sectors, but couldn't mount the partition when logging back to Ubuntu.

Any help would be appreciated.

---

### Post by cariboo on 2011-03-05
Connect the drive to a system running Windows, and run chkdsk on it. It looks like it was suffering from and unclean shutdown.

---

### Post by PRGUY85 on 2011-03-05
> **cariboo907 said:**
> Connect the drive to a system running Windows, and run chkdsk on it. It looks like it was suffering from and unclean shutdown.

I did that with no results.

---

### Post by coffeecat on 2011-03-05
> **PRGUY85 said:**
>  On GParted2 it just says unallocated space 500GB, no partition whatsoever.

You can get this if the partition table has an illegality in it. The fact that it worked in previous versions of Ubuntu and works now in Windows does not necessarily mean that this is not so. The partition table may have been OK when you tried it with a previous version of Ubuntu and Windows has an amazingly - ahem - cavalier attitude to partition tables. That is, if what you see in the Disk Management window and what the Windows installer can do is anything to go by. (Do you hear the voice of bitter experience? :rolleyes:) Something might have corrupted the partition table.

Anyway, post the output of...

```
sudo fdisk -lu
```... so that we can see.

---

### Post by PRGUY85 on 2011-03-05
Disk /dev/sda: 500.1 GB, 500106780160 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdb: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156299375 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007e5cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2          206848   117234191    58513672    7  HPFS/NTFS
/dev/sdb3       117235712   152393727    17579008   83  Linux
/dev/sdb4       152395774   156299263     1951745    5  Extended
/dev/sdb5       152395776   156299263     1951744   82  Linux swap / Solaris

---

### Post by coffeecat on 2011-03-05
Hmmm, well, that was unexpected. Your 500GB drive is showing up as sda, which is curious for a secondary drive. Whatever, you have a GPT partition table which is unusual for a drive with a NTFS partition. Fdisk doesn't really do gpt partition tables so we won't get the information I hoped for. But Gparted should be OK with a GPT partition table.

I'm somewhat out of my depth here. Was the drive pre-formatted or did you partition and format it yourself? If so, what with?

---

### Post by PRGUY85 on 2011-03-05
The drive has always been NTFS and I haven't done any partitioning or formatting since I installed it 2-3 years ago.

---

### Post by coffeecat on 2011-03-05
> **PRGUY85 said:**
> The drive has always been NTFS and I haven't done any partitioning or formatting since I installed it 2-3 years ago.

A GPT partition table would have to be a conscious choice since it's not the default in Gparted - or any of the usual Linux partitioning tools. Or perhaps it was a mbr partition table once, and has been corrupted sufficiently for it to be unusable in Ubuntu and to mislead fdisk, even though Windows is carrying on cheerfully with it. But that doesn't surprise me because in certain circumstances Windows will cheerfully corrupt the partition table for you - at no extra expense. :|

If that was my drive and I was sure that was a mbr partition table once upon a time, I'd back up the data from Windows and then create a new partition table with Gparted before creating a new NTFS partition and then restoring all the data.

I'll get someone else to have a look at this thread for another perspective. It's intriguing.

---

### Post by Quackers on 2011-03-05
This doesn't look right :-)
```
Disk identifier: 0x00000000

```
It is often an indicator that the partition table is invalid, it seems.
As coffeecat says, if you can access the drive at all, backup the data and reformat would be my suggestion.

---

### Post by PRGUY85 on 2011-03-05
> **Quackers said:**
> This doesn't look right :-)
```
Disk identifier: 0x00000000

```
It is often an indicator that the partition table is invalid, it seems.
As coffeecat says, if you can access the drive at all, backup the data and reformat would be my suggestion.

OK, let's see what I can do about it. Thanks.

---

### Post by coffeecat on 2011-03-05
> **Quackers said:**
> This doesn't look right :-)
```
Disk identifier: 0x00000000

```It is often an indicator that the partition table is invalid, it seems.

Oh, well spotted! :) As one of my experiments I've completely blanked a HD and then run fdisk (as you do) and come up with that zero disk identifier, so you'll get that with a completely non-existent partition table as well. Not the case here, granted, but evidence for a somewhat unhealthy partition table methinks.

---

### Post by PRGUY85 on 2011-03-05
> **coffeecat said:**
> Oh, well spotted! :) As one of my experiments I've completely blanked a HD and then run fdisk (as you do) and come up with that zero disk identifier, so you'll get that with a completely non-existent partition table as well. Not the case here, granted, but evidence for a somewhat unhealthy partition table methinks.

So same solution remains? Backup everything, format?

---

### Post by macroshaft on 2011-03-05
> **coffeecat said:**
> Oh, well spotted! :) As one of my experiments I've completely blanked a HD and then run fdisk (as you do) and come up with that zero disk identifier, so you'll get that with a completely non-existent partition table as well. Not the case here, granted, but evidence for a somewhat unhealthy partition table methinks.

The OP sasys ubuntu is seeing the drive as blank anyway, right? So that identifier is consistant with the symptons being experienced.

---

### Post by coffeecat on 2011-03-05
> **macroshaft said:**
> The OP sasys ubuntu is seeing the drive as blank anyway, right? So that identifier is consistant with the symptons being experienced.

The OP also says that Windows is reading the "blank" drive just fine, so I think you missed something there. Neither did you read the whole thread.

---

### Post by coffeecat on 2011-03-05
> **PRGUY85 said:**
> So same solution remains? Backup everything, format?

That's what I would do, but you need to recreate the partition table before creating any partitions. You can do this from the Device menu in Gparted.

---

### Post by macroshaft on 2011-03-05
> **coffeecat said:**
> The OP also says that Windows is reading the "blank" drive just fine, so I think you missed something there.

No I didn't, you said that identifier will show up for a blank drive and the drive is showing up in ubuntu as being blank so that makes sense. The fact that windows can read it is neither here nor there. Ubuntu believe the drive is empty so it's showing up in the way that it is.

---

### Post by coffeecat on 2011-03-05
> **macroshaft said:**
> No I didn't, you said that identifier will show up for a blank drive and the drive is showing up in ubuntu as being blank so that makes sense. The fact that windows can read it is neither here nor there. Ubuntu believe the drive is empty so it's showing up in the way that it is.

I suggest you read the whole thread. My completely blanked drive is entirely irrelevant - just a bit of joshing with Quackers.

---

### Post by macroshaft on 2011-03-05
> **coffeecat said:**
> I suggest you read the whole thread. My completely blanked drive is entirely irrelevant - just a bit of joshing with Quackers.

I really don't think you're understanding what I'm saying. Forget it.

---

### Post by srs5694 on 2011-03-05
First, the "Disk identifier: 0x00000000" thing is not a problem. In MBR, the disk identifier is just a serial number of sorts. It's often set to a random value, but it doesn't have to be, and some (mostly very old, IIRC) partitioning tools zero it out. More importantly, this value is often zeroed out on GPT disks, and in that context it's perfectly normal. Since fdisk thinks this is a GPT disk, I'd say this isn't an issue.

Second, before backing up, repartitioning, and restoring, I recommend running three more diagnostic commands (one of which will require installing additional software; see below):

```

sudo parted /dev/sda print
sudo gdisk -l /dev/sda
ls -l /dev/sda*

```

The first of those commands shows us what GNU Parted thinks of the disk. Like GParted, GNU Parted is based on libparted, so I expect it will claim that the disk is empty; but it's also likely that parted will display additional error messages that may provide a clue about what's going on.

The second command requires you to install my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) package. Download it from [its Sourceforge page](http://sourceforge.net/projects/gptfdisk/files/) (get the latest .deb package for your architecture -- probably i386 or amd64). The version in the Ubuntu repositories is quite elderly, although AFAIK it has no bugs that will cause problems for this simple use. If the GPT data are all intact, gdisk will display the partitions, much as fdisk would if this were an MBR disk. My suspicion is that you'll get some messages about some problems of one sort or another -- perhaps a damaged primary or backup partition table. If so, repair will probably be possible, but I'll need to see the output to provide further advice. (Please post the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility.)

The third command shows us what partitions the Linux kernel believes are on the disk. It's conceivable that Linux is detecting the partitions but that something else is causing them to not mount. Knowing whether the partitions are visible to the kernel is the first step in diagnosing the problem if this is what it is.

---

### Post by coffeecat on 2011-03-05
> **macroshaft said:**
> I really don't think you're understanding what I'm saying. Forget it.

I was posting in haste earlier so I was perhaps not as clear as I should have been.

When I blanked out my drive I zeroed it out completely = no partition table, no partitions, no filesystems, no files. It was simply an interesting observation that I got the same Disk identifier: 0x00000000 as the OP. 

But the OP's situation is quite different. The OP doesn't have a blank drive, simply that Gparted is showing it as unallocated. That's a bug in Gparted - it shows unallocated when there is a problem with the partition table. It's not unallocated at all - there is a partition table and there is a partition, except there is also clearly a problem. And most definitely does the OP not have a blank drive. Blank drive != drive showing as unallocated in Gparted.

Anyway, srs5694 has now posted, and I will always defer to him on the subject of partition tables.

---

### Post by macroshaft on 2011-03-05
> **coffeecat said:**
> I was posting in haste earlier so I was perhaps not as clear as I should have been.

When I blanked out my drive I zeroed it out completely = no partition table, no partitions, no filesystems, no files. It was simply an interesting observation that I got the same Disk identifier: 0x00000000 as the OP. 

But the OP's situation is quite different. The OP doesn't have a blank drive, simply that Gparted is showing it as unallocated. That's a bug in Gparted - it shows unallocated when there is a problem with the partition table. It's not unallocated at all - there is a partition table and there is a partition, except there is also clearly a problem. And most definitely does the OP not have a blank drive. Blank drive != drive showing as unallocated in Gparted.

Anyway, srs5694 has now posted, and I will always defer to him on the subject of partition tables.

And I was saying it's very possible that his system is showing the same identifier as part of that very same bug. Can we talk about something else now please? This is entirely beside the point and not going anywhere.

---

### Post by kaffelars on 2011-03-07
macroshaft:

I think I have the same issue - Natty doesn't see my Windows 7 partition, and it won't read my external hard drive or my digital camera. All of these work perfectly in Windows 7 on the same computer, and in 10.10 on another computer.

Not sure where to begin looking.. :(

---

### Post by srs5694 on 2011-03-07
> **kaffelars said:**
> macroshaft:

I think I have the same issue - Natty doesn't see my Windows 7 partition, and it won't read my external hard drive or my digital camera. All of these work perfectly in Windows 7 on the same computer, and in 10.10 on another computer.

Not sure where to begin looking.. :(

Please start a new thread. In it, include the output of the following command, typed in a Linux Terminal window:

```

sudo fdisk -lu

```

Note that's a lowercase L, not a digit 1, in "-lu". Post the results between a [noparse]```
[/noparse] string and a [noparse]
```[/noparse] string. This will provide us with information we'll need to begin diagnosing the problem. Note that similar, or even identical, symptoms can have very different causes, so your problem may be completely unrelated to PRGUY85's problem.

---

### Post by PRGUY85 on 2011-03-07
I solved this issue with TesdDisk on Win7. I did a quick search on the hard drive, then a deeper search. Showed two partitions, one of them was the one I was looking for, the other one I had never even created. I set the correct partition to primary (after checking if my files were there), deleted the other one and wrote a new partition table.

That solved it.

---

