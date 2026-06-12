---
title: "Mp3 player blues... Firmware change for Linux?"
date: 2011-02-04
forum: Multimedia Software
---

### Post by cracker89 on 2011-02-04
I bought a cheap-*** mp3 player today...it looks like this, infact it IS this model by some company called "Enter."  Its a 2gb player... very basic.
[ATTACH]182673[/ATTACH]
As it turns out, theyre untraceable on the internet...

Anywho, this is how it went down:

I got it and listened to the two stupid songs that were on it on my way home, it was working pretty good, I was happy. I got home and connected to my Ubuntu laptop, and then after deleting the songs, god knows what possesed me, but I #$#$%@$ %@@# Formatted the thing. It showed a free space of 2.0gb at the tiime..

Bear with me,

On formatting, something went wrong and the mounted disk of the thing disappeared from the screen. I opened the disk utility, and it appeared there as a "generic audio device," with 2.1gb of unallocated space. So I took all that, formatted it without partitioning and BECAUSE it wouldnt format it to FAT or NTFS, which I am guessing was the original FS, I formatted it to Ext4.

Now it wont play anything I put onto it, even tho it mounts... Help! I know one posiible soln is to format it with a windows pc, and I will too once someone confirms that...

Also, is it possible that I have formatted all the firmware and everything that made this lil piece of trash tick? That it is now completely ruined, because I cant find the firmware anywhere... 

AND, this is what I really eventually wanted to do with the thing later on when I was free-er, is there a way to change the firmware to something open source and linux friendly?

---

### Post by NFblaze on 2011-02-04
The firmwares are usually stored somewhere else away from the music storage area.

Curious enough you said it wouldnt format to FAT32 (which is most likely the filesystem.)

Why is that? What tool were you using to do that.

I'd try to format it again using something like GParted. Then give it another go.

---

### Post by cracker89 on 2011-02-04
I used the default disk utility with ubuntu, under administration>.
It wont, it gives an error saying something like,'not enough chunks for a fat32.'

I'll give it a shot...

---

### Post by NFblaze on 2011-02-04
Perhaps, it was FAT16. I cant imagine what else.

An actualy better idea would be to do a filesytem/partition recovery then. Testdisk can do this.

---

### Post by cracker89 on 2011-02-04
arright! using testdisk as i type this out... thanks man. hopefully this will have me back with music playing abilities...

---

### Post by cracker89 on 2011-02-04
hmmm.... testdisk just told me in 16 lines that it is ext4.

Meanwhile, here's the error from disk util:
```

Error creating file system: helper exited with exit code 1: helper failed with:
WARNING: Not enough clusters for a 32 bit FAT!
mkfs.vfat: Attempting to create a too large file system

mkfs.vfat 3.0.7 (24 Dec 2009)

```


what could tht filesys be?  :(

---

### Post by cracker89 on 2011-02-04
help me make sense of this?

i tried to make an ntfs part...

```
Error creating partition: helper exited with exit code 1: In part_add_partition: device_file=/dev/sdc, start=0, size=1972671049, type=0x07
Entering MS-DOS parser (offset=0, size=2124414976)
MSDOS_MAGIC found
looking at part 0 (offset 0, size 0, type 0x00)
new part entry
looking at part 1 (offset 0, size 0, type 0x00)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
Warning: Device /dev/sdc has a logical sector size of 4096.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

got it
got disk
Error: Can't have a partition outside the disk!
ped_partition_new() failed

```

---

### Post by NFblaze on 2011-02-04
[Testdisk]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery") was suggested as means to be used to try to restore previous filesystems/partitions that were deleted. In that case it would be to search for a previously created FAT file system table.

By that I mean forget about using GParted or parted.

Also, interesting of note. Your post said that the player has a sector sizes of 4096 and I was reading in [this]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9896823&postcount=13") post that GParted/parted do not support sector sizes that large for FAT filesystems. It lists a remedy by using fdisk. Though I would attempt to use Testdisk to recover the previous file system first.

---

### Post by cracker89 on 2011-02-04
i tried testdisk to recoveer the partition, but as i said, it just kept on showing ext4, no fat's showed up ever...! and yes, I guessed that 4096 isnt the supported bit... fdisk eh?
ill give tht a shot too by montgomery's left nipple!

---

### Post by cracker89 on 2011-02-04
> **NFblaze said:**
> [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Partition_table_recovery") was suggested as means to be used to try to restore previous filesystems/partitions that were deleted. In that case it would be to search for a previously created FAT file system table.

By that I mean forget about using GParted or parted.

Also, interesting of note. Your post said that the player has a sector sizes of 4096 and I was reading in [this]("http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9896823&postcount=13") post that GParted/parted do not support sector sizes that large for FAT filesystems. It lists a remedy by using fdisk. Though I would attempt to use Testdisk to recover the previous file system first.


You know,. all the helps im getting from you man. and you seem to know your stuff. thankss... I got a lot farther, even tho i didnt understand much from the other thread, i did get far as formatiing to a Fat16, however, my system wont mount it... 

I dont know what to do... I wish I could just give u the drive and tell u to whatever.. anywho, still toying around with it... thanks a bunch NFblaze

---

### Post by cracker89 on 2011-02-04
Big shout out to nfblaze and whoever that person on the other thread!

---

