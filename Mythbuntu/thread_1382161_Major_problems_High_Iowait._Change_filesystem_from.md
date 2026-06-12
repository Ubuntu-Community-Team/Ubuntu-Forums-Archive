---
title: "Major problems: High Iowait. Change filesystem from etx4 to xfs/ext3/jfs?"
date: 2010-01-15
forum: Mythbuntu
---

### Post by yussu on 2010-01-15
Hello, 

been running Myhtv for five years without major problems, but now after I upgraded my system to HD capaple and doing an clean Myhtbuntu 9.10 install I´m having major problems which I cannot seem to be able to solve. 

The problem is periodical overall system slugginesh most likely caused by High IOWait. What causes the high IOWait I have no idea but I suspect it might be the filesystem, EXT4.

Hardware: 
Processor: Core Duo 2.8 GHz
MoBo: Asus P5Q-E
Ram: 4 gigabytes DDR3
Harddrive: WD caviar green 1 TB
GPU: GeForce 9600GT
Filesystem: EXT4
Mythtv: 0.22-fixes (nightly builds)

My Live TV and recordings are SD from two DVB-C cards, HD based material from videos. 

Maybe 50 % of the time the system works ok, but sometimes (mainly in the evenings?) the system performance is unbearable: perodically the playback stops for 5-15 sec (sometimes even goes back to main menu), plays fine for few secs and stops again. During this the IOWait hits 99 %, IOtop shows no disc activity. When the choppines goes away on iotop I can see some heavy activity on KJournalD2 and pdflush. When the system runs fine the processor load is around 2-10 % (VDPAU) and IOWait 0-5 %. During choppiness the processor load goes to 0 % and IOWait 99-100 %. I cannot reproduce this by anything, I can record 6 shows and watch HD video without hiccups so I doubt it´s hardware problem.

I googled this alot and tried everything I can think of. I cannot reproduce this reliably but ofcourse every time I think I have found THE solution it comes back. 

I´ve found other posts about problems regarding high IOWait and ext4 so I´m thinking about switching to other filesystem  (maybe XFS or JFS or even EXT3) to see if it has any effect. 

So far I have no idea how to do that...I would not like to do fresh install but maybe use external harddrive and rsync everything to it, convert main hard drive´s file system, rsync everything back, update grub etc. Any links how to do this are very welcome. 

Sorry for long post and poor english, any ideas are welcome!

   -Jussi

---

### Post by kbrunsting on 2010-01-15
It could be related to your WD green drive.... there are similiar posts with problems with those drives with writing to the disk and parking the heads on the drive.  I have the 1.5TB green drive with similar issues.  Some people have reported that sending it back for a newer one might fix the problem.  I just received my replacement and I'm hoping the problem is fixed.

---

### Post by movieman on 2010-01-16
I have two WD 'Green' drives in my MythTV system and no disk-related problems; however, they use ext3 and XFS.

---

### Post by yussu on 2010-01-16
Hmmpf. Really annoyed with this one. Found one promising solution but it didn't help.

"So if you have the same problem, either return your disks and get yourself some good ones or add a file called 10-{whateveryouwant}.conf to /etc/sysctl.d and add following two lines to it:

vm.dirty_writeback_centisecs=100
vm.dirty_expire_centisecs=100"

So now I´m going to try different filesystem and if it doesn't help, I maybe have to buy new harddrive. 

Anyone want to buy WD Caviar Green? Will sell it cheap :)

---

### Post by ian dobson on 2010-01-16
Hi,

Strange I have 3 2Tb WD green drives in a RAID5 array and have my recordings/mysql database on it and I'm not seeing any problems.

I've tested the array with up to 6 recordings at the same time (2 from my PVR-500 and 4 HD streams from my 2 DVB-c tuners). I currently using ext3 but I've tested ext4 on a small test array and haven't seen any problems.

Have you setup the SATA controller for AHCI/NCQ or "compatibility mode"? My backend uses an ASUS p5q and all SATA ports are setup for AHCI mode.

Regards
Ian Dobson

---

### Post by movieman on 2010-01-16
Yeah, I use AHCI too.

---

### Post by movieman on 2010-01-17
BTW, how old is this drive? I've been reading about problems with the newer revisions of the 1.5TB drive and perhaps something similar applies to new 1TB drives too. For example:

[http://community.wdc.com/t5/Desktop/WD-1-5TB-Green-drives-Useful-as-door-stops/td-p/1217/page/2](http://community.wdc.com/t5/Desktop/WD-1-5TB-Green-drives-Useful-as-door-stops/td-p/1217/page/2)

Apparently the new 1.5TB drives use a 4k sector size instead of 512 bytes, which could cause problems:

[http://opensolaris.org/jive/thread.jspa?threadID=121871&tstart=0](http://opensolaris.org/jive/thread.jspa?threadID=121871&tstart=0)

---

### Post by yussu on 2010-01-17
My harddrive is about two months old and I think i've setup the SATA controller on EHCI mode. I'm in the middle of converting the file system to EXT3 so will find out if that is the cause. Let's see how this goes...

---

### Post by yussu on 2010-01-17
Well, spent the whole day converting from ext4 to ext3. No luck, still get high IOWait and stuttering. The reason it took the whole day was that copying to and from was so slow...because the periodicl topping of IOWait :)

---

### Post by DLGandalf on 2010-01-18
I'm having the same problem, having sabnzbd downloading at a rate of 2MB/s cripples my system so much it's almost unbearable, I'm struggling with this for over a year. Is it lvm? are the bios settings incorrect? is the intel chipset buggy under linux and so on.

When I see someone posting on this, it's almost always a new intel chipset of the past 1-2 years, like P35 or P45, but that could be a coincidence

---

### Post by ian dobson on 2010-01-19
Hi,

My server backed has 2Tb WD drives and a ASUS P5Q motherboard (P45 chipset), and I'm not seeing any problems with high IO.

Have you tried disabling NCQ for your bad drives?

echo 1 > /sys/block/sda/device/queue_depth

Looking in the kernel source yesterday I saw that several WD drives are on the blacklist for NCQ due to a broken NCQ implementation. The above command disables NCQ for sda. This is a runtime configuration that you can set at anytime but it doesn't servive a reboot so if it helps add it to your /etc/rc.local.

Regards
Ian Dobson

---

### Post by yussu on 2010-01-28
Well,now I can confirm the WD harddrive really was the problem.

Replaced it with Samsung Spinpoint F3 2 TB, installed everything again (only now 64 bit) and haven't had a single problem with high IO since.

---

