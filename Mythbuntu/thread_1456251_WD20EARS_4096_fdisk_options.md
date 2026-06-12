---
title: "WD20EARS 4096 fdisk options"
date: 2010-04-16
forum: Mythbuntu
---

### Post by purduephotog on 2010-04-16
Could someone kindly point me to the documented command line option for the new 4096 drives?  I've searched and, while finding lots of fruitful discussions, have not seen a documented 'enter this' command.

I did see the GUI apparently works fine, but unfortunately due to my VNC issues (and poor quality TV) I can't run the gui.

Thanks-

Jason

---

### Post by movieman on 2010-04-17
You should be able to use parted to ensure that all but the first partition are 4k aligned: that's what I used to get the partitions aligned for my SSD. Parted does suffer from '1MB is a million bytes' silliness though, which makes alignment to power of two sectors excessively painful... AFAIR you can switch it to use real megabytes instead.

---

### Post by ian dobson on 2010-04-17
Hi,

I've just added 2 to my backend (now that sounds abit strange), just format them using fdisk from a terminal window using the -u (sector number entry) and set the start partition to a multiple of 4Kb (start at sector number 64 and not 63).

so just use fdisk -u /dev/your-harddisk and create a new primary partition starting a sector 64, thats it.

```

fdisk -u /dev/sde

The number of cylinders for this disk is set to 243201.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): p

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1786ce25

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              64  3907029167  1953514552   fd  Linux raid autodetect

```

Regards
Ian Dobson

---

### Post by movieman on 2010-04-17
That sounds easier :).

---

### Post by ian dobson on 2010-04-17
Hi,

Everything is easy when you know how to do it.

Regards
Ian Dobson

---

### Post by purduephotog on 2010-04-17
So these are the commands I ran through:

```

user@mythbox:~$ sudo fdisk -u  
[sudo] password for user: 
 
Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks
 
Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track
 
user@mythbox:~$ sudo fdisk -l
 
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
 
Disk /dev/sda doesn't contain a valid partition table
 
Disk /dev/sdb: 8002 MB, 8002732032 bytes
247 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c1264
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         971     7427072   83  Linux
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 33, 3)
Partition 1 has different physical/logical endings:
     phys=(924, 192, 36) logical=(970, 25, 62)
Partition 1 does not end on cylinder boundary.
/dev/sdb2             971        1021      385025    5  Extended
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(924, 225, 4) logical=(970, 59, 1)
Partition 2 has different physical/logical endings:
     phys=(972, 208, 4) logical=(1020, 129, 10)
Partition 2 does not end on cylinder boundary.
/dev/sdb5             971        1021      385024   82  Linux swap / Solaris

user@mythbox:~$ sudo fdisk -u /dev/sda
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x962f53fb.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.
 
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)
 
WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c').
 
Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)
 
Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p

Partition number (1-4): 1

First sector (63-3907029167, default 63): 64
Last sector, +sectors or +size{K,M,G} (64-3907029167, default 3907029167): 

Using default value 3907029167
 
Command (m for help): w
The partition table has been altered!
 
Calling ioctl() to re-read partition table.
Syncing disks.
user@mythbox:~$ 


```

Sound about right?

---

### Post by ian dobson on 2010-04-17
Hi,

I can't hear anything from my monitor but your partition starts at number 64 so it's aligned to a sector boundry so everything should be OK.

If you do a fdisk -l -u you'll see that on your new drive the partition starts at sector 64 and your old drives start as 63.

Regards
Ian Dobson

---

### Post by purduephotog on 2010-04-17
> **ian dobson said:**
> Hi,

I can't hear anything from my monitor but your partition starts at number 64 so it's aligned to a sector boundry so everything should be OK.

If you do a fdisk -l -u you'll see that on your new drive the partition starts at sector 64 and your old drives start as 63.

Regards
Ian Dobson


Thanks Ian.  You've got to put your head REALLY REALLY close... closer... closer... not that close.

Indeed that is what it says.  I'm not sure if I got the formatting to use 4096 correct or not, will have to review that later.

And now to figure out why VNC won't work.

---

### Post by HankB on 2010-07-01
I plan to use one of these drives in a Raid-1 (mirrored) with another brand drive. The other drive will not feature the larger sectors.

Should I expect this to work OK or is mixing different drives like this a Bad Idea(tm)

thanks,
hank

---

### Post by ian dobson on 2010-07-01
Hi,

Just make sure you partition the 4K drive so that the partition starts on a sector divisble by 8 (4K / 512 byte). So 64 is good.

I have 2 of these drives in a RAID0 array and haven't seen any performace problems.

Regards
Ian Dobson

---

### Post by HankB on 2010-07-26
> **ian dobson said:**
> Just make sure you partition the 4K drive so that the partition starts on a sector divisble by 8 (4K / 512 byte). So 64 is good.

Thanks, Ian.

It seemed like I needed to use 'parted' to work with partitions created by the 10.04 server install. Neither 'fdisk' nor 'sfdisk' seemed to understand the partition table:

```
root@tenere:~# echo print|sfdisk --no-reread /dev/sdb

Disk /dev/sdb: 243201 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sdb1          0+ 243201- 243202- 1953514583+  ee  GPT
		start: (c,h,s) expected (0,0,2) found (0,0,1)
/dev/sdb2          0       -       0          0    0  Empty
/dev/sdb3          0       -       0          0    0  Empty
/dev/sdb4          0       -       0          0    0  Empty
trailing junk after number

sfdisk: bad input
root@tenere:~#
``` 

'cfdisk' provided a more useful diagnostic:
```
Warning!!  Unsupported GPT (GUID Partition Table) detected. Use GNU Parted.
```



It's not obvious to me that I achieved the desired result. Here's what 'parted' says about the disk.

```
root@tenere:~# parted /dev/sdb
GNU Parted 2.2
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      17.4kB  1018kB  1000kB                        bios_grub
 2      1018kB  4001MB  4000MB  ext4                  raid
 4      4001MB  1997GB  1993GB  ext4                  raid
 3      1997GB  2000GB  3049MB  linux-swap(v1)

(parted) align-check opt 2                                                
(parted) quit                                                             
root@tenere:~#
``` 

It's somewhat academic I suppose. I'm using this for a NAS that I'm accessing over the Internet so throughput requirements are pretty low. But I'm still curious.

thanks,
hank

---

### Post by ian dobson on 2010-07-26
Hi,

use fdisk with the -u option to do sector exact partitioning.

Regards
Ian Dobson

---

### Post by Scoubidou on 2010-08-03
Hi guys,

I just installed and fdisk my WD20EARS with the instruction in this post.
Now I see this :

```
# fdisk -lu /dev/sdc

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8fd3898b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              64  3907029167  1953514552   83  Linux

```

So I guess it's been align.

Now when I try to mount the drive I get : 

```
# mount /dev/sdc /mnt/ 
mount: you must specify the filesystem type

# mount /dev/sdc /mnt/ -t ext4
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

What am I missing?

Thanks

---

### Post by HankB on 2010-08-03
> **Scoubidou said:**
> Hi guys,

I just installed and fdisk ...

What am I missing?



mkfs.ext4?

```
hbarta@cypress:~/Documents/electronics/DroidX/ringtones$ mkfs.ext4
Usage: mkfs.ext4 [-c|-l filename] [-b block-size] [-f fragment-size]
	[-i bytes-per-inode] [-I inode-size] [-J journal-options]
	[-G meta group size] [-N number-of-inodes]
	[-m reserved-blocks-percentage] [-o creator-os]
	[-g blocks-per-group] [-L volume-label] [-M last-mounted-directory]
	[-O feature[,...]] [-r fs-revision] [-E extended-option[,...]]
	[-T fs-type] [-U UUID] [-jnqvFKSV] device [blocks-count]
```

---

### Post by Scoubidou on 2010-08-03
Yeah thanks.

I used gparted to create and format the drive.

Now is it normal that I have to set the perms to 777 in order to write in my new drive?

I mounted it in /data

Thanks.

---

### Post by Mocker on 2010-08-11
I hadn't seen any discussion of this anywhere, and spent the last half an hour or so Googling and fretting over the filesystem blocksize, in addition to the partition alignment. Should I use mkfs.ext4 with a -b argument to set the block size to 4096? Shouldn't I?

Well... it looks like mkfs.ext4 is smart enough to figure it out on its own. I just did a mkfs.ext4 on a 1.5T partition on my new WD20EARS, without a block size setting and it reported:

```
Block size=4096 (log=2)
```

So, looks like the software can figure that bit out for you.

---

### Post by ian dobson on 2010-08-12
> **Mocker said:**
> I hadn't seen any discussion of this anywhere, and spent the last half an hour or so Googling and fretting over the filesystem blocksize, in addition to the partition alignment. Should I use mkfs.ext4 with a -b argument to set the block size to 4096? Shouldn't I?

Well... it looks like mkfs.ext4 is smart enough to figure it out on its own. I just did a mkfs.ext4 on a 1.5T partition on my new WD20EARS, without a block size setting and it reported:

```
Block size=4096 (log=2)
```

So, looks like the software can figure that bit out for you.


I think 4K is the normal cluster size/block size for the ext(2,3,4) file systems. That fits very well with the page size on Intel systems. Have a look here :- [http://lwn.net/Articles/266274/](http://lwn.net/Articles/266274/) it may be abit heavy reading.

Regards
Ian Dobson

---

### Post by jeffers.r on 2010-08-17
> **ian dobson said:**
> Just make sure you partition the 4K drive so that the partition starts on a sector divisble by 8 (4K / 512 byte). So 64 is good.

Hey Ian,

I'm curious if you could provide any additional info on this. While I initially thought that setting the start sector to a number that is divisible by 8 was sufficient, based on [this article]("http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=5655") from WD, it says to "Make sure that all partitions start on a multiple of 8 sectors (8x 512B =  4KB) and that partition sizes are multiples of 8 sectors." In other words, your end sector should also be deliberately set to ensure that:

(Start Sector - End Sector) / 8 = round number

Is this not the case? I've found that setting only the start sector didn't help correct performance issues related to a misaligned drive.

---

### Post by ian dobson on 2010-08-17
Hi,

I'm not sure. Thinking about it, if the partition is aligned to a 4K boundry and you format it with ext4 for example (which uses a 4K block size). If your partition istn't exactly divisable by 4K then mkfs won't be able to use the last X sectors on the drive.

I can only think that the size requirement is there if you have multiple partitions (so that the second partition also starts on a 4K boundry.

Maybe if I get abit of time I'll have a play with a spare drive that I have.

Regards
Ian Dobson

---

### Post by thaMANSTA on 2010-09-30
deleted

---

### Post by thaMANSTA on 2010-09-30
Just got one of these to add to a RAID array.  Made sure the start of the partitions are all divisible by 8, still getting this error on the first partition, not sure why?

```

~# fdisk -lu /dev/sdi

Disk /dev/sdi: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce08e649

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1              64       21167       10552   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdi2           21168  1953525167   976752000   fd  Linux raid autodetect
/dev/sdi3      1953525168  3907029167   976752000   fd  Linux raid autodetect
~#
```Here is the drive it's paired with:
```

~# fdisk -ul /dev/sda

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6d26f37c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       16064        8001   83  Linux
/dev/sda2           16065  1953520064   976752000   fd  Linux raid autodetect
/dev/sda3      1953520065  3907024064   976752000   fd  Linux raid autodetect
~#
```

---

### Post by ian dobson on 2010-09-30
Hi,

Your paired drive isn't partitioned the same as the new drive:-

/dev/sdi1              64       21167       10552   83  Linux
/dev/sda1              63       16064        8001   83  Linux

Regards
Ian Dobson

---

### Post by thaMANSTA on 2010-09-30
> **ian dobson said:**
> Hi,

Your paired drive isn't partitioned the same as the new drive:-

/dev/sdi1              64       21167       10552   83  Linux
/dev/sda1              63       16064        8001   83  Linux



Yeah, the new drive is a WD20EARS, old one is not.  I was making sure that the partitions all started on multiples of 8, but it's still complaining about the first partition on the WD20EARS.

---

### Post by ian dobson on 2010-09-30
Hi,

OK fdisk is complaining that the first partition doesn't end on a cylinder boundry.

3907029168/243201=16065 (sectors/cylinders=sectors per cylinder)

So I'd imagine that fdisk won't complain if you set the start sector to 63 and the last to 16064, but being a 4K drive your alignment won't be correct. But if you set the start to 64 the alignment will be correct but it might be too small (by 512 bytes for the array).

I always make sure I get the same drives for my arrays/never use 100% of the drives. I usually leave 1-2% unused at the end of the drive so I can play with the partition sizes if needed.

Regards
Ian Dobson

---

### Post by LowSky on 2010-09-30
I'm using a WD2001FASS (2TB black) and I partitioned it using gparted (point and click partion setup) and it seems to work fine, with no performance issues.

When I tried to use it for cloning another drive it did have the issue of not ending on a cylinder boundry.

---

### Post by psusi on 2010-09-30
Ignore the warning about cylinder boundaries; it has been meaningless gibberish for years.  Recent versions of (g)parted automatically align the partition to a 1 MB boundary like Windows now does to get good alignment on broken drives like the WD EARS series that do not report their sector size correctly.

---

### Post by HankB on 2010-09-30
> **ian dobson said:**
> ...
I always make sure I get the same drives for my arrays
I always mix up the drives between brands in case there is a bad run or a particular model encounters systematic failures.

---

### Post by srs5694 on 2010-09-30
As psusi says, the "error" message isn't an error; it's just a notification, and one that's unimportant unless you're using some *very* old hardware or software -- say, stuff that was current when Windows 3.1 was released.

Your partition sizes on the two drives are identical, according to the fdisk output you've posted, so you needn't worry about the size issues ian dobson mentions. Using the same model drives in a RAID array can simplify configuration, but it's not strictly necessary, and your setup looks fine to me.

In other words, theMANSTA, you're good to go.

---

### Post by ian dobson on 2010-09-30
> **srs5694 said:**
> As psusi says, the "error" message isn't an error; it's just a notification, and one that's unimportant unless you're using some *very* old hardware or software -- say, stuff that was current when Windows 3.1 was released.

Your partition sizes on the two drives are identical, according to the fdisk output you've posted, so you needn't worry about the size issues ian dobson mentions. Using the same model drives in a RAID array can simplify configuration, but it's not strictly necessary, and your setup looks fine to me.

In other words, theMANSTA, you're good to go.

So can you please explain to be how these two partitions are the same size:-

```

Device Boot      Start         End      Blocks   Id  System
/dev/sdi1              64       21167       10552   83  Linux

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       16064        8001   83  Linux
```

Looking forward to your answer.

Regards
Ian Dobson

---

### Post by psusi on 2010-09-30
That partition isn't part of a raid, so it doesn't matter.

---

### Post by srs5694 on 2010-09-30
> **ian dobson said:**
> Looking forward to your answer.

My answer is the same as psusi's, but I'll add that I apologize for not being clearer in my earlier post. I should have written "your ***RAID*** partition sizes on the two drives are identical, according to the fdisk output you've posted" (emphasis added for what I should have included but didn't).

---

### Post by ian dobson on 2010-09-30
Hi,

OK, yes your right.

Regards
Ian Dobson

---

