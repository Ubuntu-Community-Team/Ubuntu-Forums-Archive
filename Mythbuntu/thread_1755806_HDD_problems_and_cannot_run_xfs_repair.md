---
title: "HDD problems and cannot run xfs_repair"
date: 2011-05-11
forum: Mythbuntu
---

### Post by dibuntux on 2011-05-11
Hi all, I'm on 0.24 with latest PPA. I was recording from 3 different input, then started to watch one of the recordings meanwhile recording; nothing unusual.
Then the system started to lag for several seconds, many times - then stopped and become unresponsive.
I had to stop it forcefully, in a bad way - reset.
Today I found that the system still was unresponsive and decide to defrag the XFS file system, which was indeed 24% fragmented. After the defrag the system still was slow.
I decided to try xfs_repair (since SMART tool found 2 bad sectors on the disk) but I was unable to run it.
As soon as I enter the command 
sudo telinit 1
mythbuntu show its logo and then stops there, without any prompt.
At boot I get no ESC options to get to a command prompt, so how can I enter single user mode and umount the XFS partition and then run xfs_repair ?

Any ideas? TIA



Mythbuntu 10.04 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen X 2 
Skystar 2 DVB-s
Nova T-500 dual DVB-T
Denon AVR 1610 connected with SPDIF
Optoma HD700x on DVI
dibuntux is online now Report Post   	Edit/Delete Message

---

### Post by ian dobson on 2011-05-11
Hi,

Press/hold the shift key just as grub is loading, that should bring you to the grub boot menu. Then boot in single user mode and run the repair.

Regards
Ian Dobson

---

### Post by dibuntux on 2011-05-11
Ian, my friend, thanks for your fast help. I'll try that tomorrow, now it is late in the evening and it seems to be working... time to watch some tv.

---

### Post by nickrout on 2011-05-12
or boot from a livecd and run the repair program

---

### Post by dibuntux on 2011-05-12
nickrout: if you boot into livecd there's no xfs support...thanks anyway

Ian: I pressed the shift and got to the grub menu as you stated, great!
Then I found that even on just started system could not umount my xfs partition. So I found I had to use:
umount -l /dev/sda5
to unmount the xfs, and then i could run
xfs_repair /dev/sda5
The program run 7 stages, did a lot of things in less than a minute and stated that the system is ok.

Still, on 0.23 I was able to record 3 shows (all SDTV in DVB) at a time and watch one of them in time shift without having consistent lags and disk fragmentation. Maybe the disks where just empty? Still I got 700 MB free on my primary 1,5TB disk and 400 MB on my secondary disk. And of course I use storage groups for recordings and livetv.
What are the limits of Myth considering my HW, which I believe is adequate?

---

### Post by ian dobson on 2011-05-12
Hi,

Maybe edit your grub defaults file so that the boot menu is always displayed for afew seconds ***.

Ouch only 700+400Mb free, I'm thinking your my next update for my large (8Tb RAID5 array). I would imagine 2 recordings and 1playback at the same time. I can record 4HD programs at the same time without too much load.

I don't have any experiance with xfs, I've only ever used ext3/4. I've just seen alot of threads where xfs screwed up and the repair program won't run for whatever reasons.

Regards
Ian Dobson

EDIT:
*** edit /etc/default/grub change the start of the file to
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=1

then run update-grub

---

### Post by dibuntux on 2011-05-12
Dear Ian, I remember that you have that nice RAID5 array with 2 TB drives; RAID5 bandwidth should be at least twice of that of a single disk. But still, with two disk, the load on one disk at maximum should be 2 recording in SD and watching one of them on time shift - not too much.
I'm now running a SMART selftest that is taking way too long; SMART report 2 bad sectors. Is it possible that the load has created a fault on the disk?

As for XFS... before EXT4 was considered perfect for multimedia, and I always used that for myth. Maybe I will reconsider when time will come for me to build a RAID5 for myth.
I have a RAID1 on my main pc that is up and running since Ubuntu 7.10...

Thanks

---

### Post by LowSky on 2011-05-12
I can record 5 HD shows and watch one on a busy night without breaking a sweat, and NO RAID here. Sure my hardware is a bit better (Phenom II x4 and Nvidia 460 GTX)), but you should be able to do very close to the same.

I didn't think XFS could become so fragmented. I used it in the past but when I decided to upgrade I stayed with EXT4. I'm also betting your drive issue is due to the free space.... start deleting or buy another drive. 2TB is under $100 these days.

You really should have more free space on those drives. I set MythTV to keep about 10 GB free at all times. I also set many shows to only keep up to 5 recordings of a single show, unless I'm a huge fan and want to keep it for later, then many of them are set to expire. Way back I had an issue where I was using a single disk system and mythtv recorded too much to my drive running anything became an issue. I found keeping 10 GB free helped considerably. Especially if you do a lot of ripping or normal computing on the same machine.

---

### Post by dibuntux on 2011-05-12
Ian, sorry to confuse you - I made a VERY dumb mistake: I meant 700 and 400 GIGA BYTE of free space, not MB... ahahahaha, sorry!

So the the 2 disks are one half full and the other 1/5 full! Definitely there is space. The self test did not terminate, so I had to kill it. Everything is reported to be ok, no fragmentation and disk clean, but still now I have 4-5 seconds lags on every operation, like showing the schedule.
Very strange, the only thing I can think of to solve the problem is a reformat of the partition, but I have to find space for 700 GB of data... I know disks are cheap...

Thanks again and sorry for my mistake!

PS: LowSky, sorry to confuse you too and thanks for helping!

---

### Post by ian dobson on 2011-05-12
Hi,

I normally say 1 HD or 2 SD recording per modern harddisk (it doesn't metter if they're in an arry or not).

I would rerun the xfs-repair script and maybe try defragmenting your xfs partition. If you get round to buying a new harddisk, have a look at using ext4. ext4 supports delayed allocation which should reduce fragmentation (Only allocate space on the disk when it's written, rather than allocating individual blocks when an application writes data), also ext4 support fast deletes unlike ext3.

Regards
Ian Dobson

---

### Post by nickrout on 2011-05-12
Is your database OK? Take a look at the tables in mythweb and see if any are broken.

---

### Post by dibuntux on 2011-05-12
Dear nickrout, I checked the database (extended check and optimize tables) and all is OK.

Will do some more testing... I will let you know

---

### Post by dibuntux on 2011-05-13
My system is now very slow. At times. It seems like that when the disk is reading some sectors it blocks reading them forever. So, it works normally until the HDD LED is steady on and everything freeze from 3-4 seconds to 10-30 seconds. Then it goes on normally until it happens again.

I deleted some 100 GB of files. I defrag the disks, but no fragmentation. 
I run two more times xfs_repair and it says that the disk is ok.
I've been running a SMART selftest (from disk utility) that should be 10 minutes and it is now 6 hours and does not complete. SMART says the disk is OK, but has 2 bad sectors.
I believe that with a format of the partition I will solve the problem... but I have some 700 GB of data that I do not know where to put. Besides, the /home is mapped to the partition, so I'm not sure which approach I will have to take. 

Mmmmh, any suggestions? TIA

---

### Post by nickrout on 2011-05-14
does dmesg have any dire messages about the disk? It sounds to me as if the disk is on its way out. If so, don't mount it rw again.  Get a new disk, boot via a usb stick or cd and copy all your valuable data to the new drive.

---

### Post by dibuntux on 2011-05-15
Probably the disk has HW problems; but I want to give it a try with a re-format, this time using EXT4 instead of XFS as Ian suggested.

So now I'm moving all the videos data on disks & PCs around the house; then I'll make a backup of /home (with recs and the rest) onto the other disk. Then I'll reformat & check the new partition, finally restore and see if it works.
Any suggestions to improve this operation? TIA

PS: if I backup, reformat the /home partition and restore, then I will have to modify /etc/fstab to modify the UUID of the new device for /home in order for the system to find everything at reboot, right?

---

### Post by nickrout on 2011-05-15
yes I think the uuid will change, you can get the uuid by running```
 sudo blkid
```

---

### Post by dibuntux on 2011-05-18
The story goes on. I downloaded Data Life Diagnostic from WD and did extended check & repair; errors were found & repaired.
Reinstalled the system: no luck, in the end the disk is not able to reboot "/dev/sd1 is missing..." (still I want to try the "write 0 to all disk sectors" option)

So I got a new WD 2 TB drive and wanted to do a RAID1 for my system. I started with the Mythbuntu CD, downloaded Disk Utility, Gparted and mdadm and created md device for /, /home & swap, sync and formated them & launched the installer.

The installer found the md device and installed on them, but at the end could not install GRUB onto the disks.

Erased the array and installed onto a single disk; grub install correctly.

It is evident that something is wrong in my procedure or in the mythbunt installer on RAID device.

I know how to do it with ubuntu, using the alternate installer, but then I will have an ubuntu system and not mythbuntu.

Any idea? TIA

PS: btw, xfs and xfs_repair were not the problem after all...

---

### Post by nickrout on 2011-05-18
Do a ubuntu alternate install and then ```
sudo aptitude install mythbuntu-desktop
```

---

### Post by dibuntux on 2011-05-18
Thank you nick! But, in this way will I be on xfce or gnome, and will all mythbuntu packages be installed?

---

### Post by nickrout on 2011-05-18
You will have a choice of xfce or gnome when you log in, xfce is a dependency of mythbuntu-desktop so will be installed with the above command. And yes i believe you will get all the mythbuntu packages (plus some ordinary ubuntu ones you probably don't need).

Other approach might be a server install, which is pretty minimal, then install mythbuntu-desktop. That way you should avoid ubuntu (gnome) desktop. I assume there is an alternate server install cd (?)

---

### Post by dibuntux on 2011-05-23
Dear friends, just wanted to let you know the end of the story, which is quite interesting.

I managed to install a RAID1 system using the Ubuntu alternate disk; the result is the same I got using standard Mythbuntu LiveCD and Disk Utility (and mdadm) to create a RAID1 first.

I could not install succesfully a bootloader becouse disk geometry was not the same: 1 WD500 GB & 1 WD 2 TB. Different sectors size and for a mirror does not sync...I guess. This should be no problem for a RAID5 array... any Idea?

BTW, the original WD 1.5 TB... it is now working again. I tried the "Write 0 to disk" function from the WD Datalife diagnostic and it correctly erased the whole disk. I could then create a partition, checked it, and run SMART self test: disk is healty with NO BAD sectors.

Doing some investigation, I found that the kind of error I got was a scrambling of the firmware area of the disk or other restricted area; writing zeros to the disk solved the problem to an otherwise unformatable, unrecoverable disk.

But, beware, normal Mythbuntu operation (well, if recording 3 shows SD and watching a 4th is normal) created the condition for this.

Now I find my system with:
WD 500 GB - system disk, music, pictures, livetv & recordings
WD 2 TB - videos, livetv & recordings 
WD 1.5 TB - emtpy ext4 partition

I also enabled AHCI instead of IDE, this will add NCQ (directly from wikipedia):
Native Command Queuing (NCQ) is a technology designed to increase performance of SATA hard disks under certain conditions by allowing the individual hard disk to internally optimize the order in which received read and write commands are executed. This can reduce the amount of unnecessary drive head movement, resulting in increased performance (and slightly decreased wear of the drive) for workloads where multiple simultaneous read/write requests are outstanding, most often occurring in server-type applications.

Now the tentation is to buy disk n.4 (1.5 TB) and make a RAID5 using 1.5 partitions and leaving a 500 MB partition on the 2 TB disk to backup the system disk.
Any suggestions? TIA

Hope all this mess described will be of anyhelp to others!

---

### Post by ian dobson on 2011-05-23
Hi,

I can't imagine that recording several programs at the same time could cause a problem for the drives. I quite often end up recording several programs at the same time and I've recorded well over 5Tb since 2008 and saved about 2.5Tb for rewatching (I'm a sci-fi fan and just love the old StarTrek).

Regards
Ian Dobson

---

### Post by nickrout on 2011-05-23
it's not one of the drives with 4k blocksize is it? If you don't partition them right, you'll get bad performance.

---

### Post by dibuntux on 2011-05-24
Ian, well, ok, maybe it is not Myth, it is just the drive. Now it lies on my HTPC with this empty 1.5TB ext4 partition... do not know what to do with it. Can you resume for me the scheme of your drives? (btw, great minds do think alike: I believe I watched ALL StarTrek episodes of all series)

Nick: yes it is one of those - I used Gparted to make one big ext4 - do I need to do something else?

---

### Post by ian dobson on 2011-05-24
Hi,

My drive/fs setup is really simple. I have 4 wd20eads (2Tb 512byte drives), they're all partitioned with a 20Gb boot/root (then mirrored through mdadm) and the rest are partitioned/combined to a RAID5 array.

My system still boots with grub1 so root/boot can't be on a RAID5 array, so the system boots from /dev/sda1 which is the first drive in the mirror. I use the kernel commandline root=/dev/md0 to get linux to mount the mdadm array as root, but grub still loads from /dev/sda1. Being a mirrored array /dev/sda1 and /dev/md0 look the same/file systems are the same so linux can load it's inital ram disk from /dev/sda1 then switch over to /dev/md0 without even seeing a difference.

I hope this makes some sense to you. My brain seems to be stuck in German at the moment.

Regards
ian Dobson

---

### Post by dibuntux on 2011-05-24
Thanks for remebering to me your disk structure. On my main PC I have 2 WD 400 GB with GRUB 1.5 in RAID1. There are 3 partitions:/, /home & swap, all as md devices. GRUB is installed on both disks as per standard ubuntu RAID installation, so that if one disk fail, the system will boot from the other disks. I also have a fourth partition on both disks, configured as RAID0 (stripe), for fast video editing.
I tried to replicate RAID1 with my 500 GB and 2 TB disks, but could not install GRUB.

My disks are:
WD 500 GB WD5000AADS - system disk, music, pictures, livetv & recordings
WD 2 TB WD20EARS- videos, livetv & recordings
WD 1.5 TB WD215EARS- emtpy ext4 partition

Yours is WD20EADS; is the same drive as mines with 32 MB of cache instead of 64 MB. Guess mine also is 512 bytes per sector and not the dreaded 4K.

Any suggestion on what to do with this kind of disk structure?

---

### Post by nickrout on 2011-05-24
Ahh OK well let us have the output of ```
sudo fdisk -l 
```

---

### Post by ian dobson on 2011-05-24
Hi,

The eads drives are 512byte sector drives, and the ears are 4K sector drives. So you 2Tb drive is a 4k drive. But that's not a problem, just manually partition is so the fs starts on a 4k boundry (sector 64 for example) using fdisk -u

You have a really strange mix of drives, not sure the best way to use them. Maybe no raid, just manually copying the data to other drives for backup.

Regards
Ian Dobson

---

### Post by dibuntux on 2011-05-25
Well, thanks to nick's suggestion this is the output of fdisk -l:


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001fb46

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2930      243201  1929984840    5  Extended
/dev/sda5            2930      243201  1929984808+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00084eb0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60671   487338783+  83  Linux
/dev/sdb2           60672       60801     1044225    5  Extended
/dev/sdb5           60673       60801     1036192+  82  Linux swap / Solaris

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00057a59

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      182401  1465136001   83  Linux


So ALL disk have 512 bytes sectors. Then why I could not install on RAID1 - either with Mythbuntu LiveCD + Disk Utility + mdamd or Ubuntu Alternate standard RAID1 proc as per Ubuntu wiki?

I know that disk may not be identical, if the specs are close; here we got all drives of the same family, same sector size.

It is a strange drive mix, I know. I bought the first Wd 500 GB because it was cheap at the time and available. Then, when I realized that 500 GB were not enough, 1.5 TB drive was the best price/capacity I could get. Finally, after the recent failure (and considering the 1.5 TB dead), 2 TB seemd to be most convenient to buy. So the orrendous mix.

I really would like to have a mix of RAID1 & RAID5 like you, Ian.
Are you satisfied with performance? Any lag on operations, like recordings & watching TV?

---

### Post by ian dobson on 2011-05-25
Hi,

I can record 6 programs and watch a 7th at the same time before myth-backend starts getting I/O bound, having 16Gb ram really helps there.

If you want to use raid then why not setup mdadm to use partitions rather than block devices. My backup array is just a span of 3 2tb 4k wd drives, at seems to work without any problems. The write speed seems to be about 160Mb/sec which is more than enough.

Regards
Ian Dobson

---

### Post by dibuntux on 2011-05-25
Very interesting. I think I've always used partitions to setup RAID with mdadm. Infact I never used the mdadm directly but by means of ubuntu installation or Disk Utility, and I think they both use partitions.

I've only 2 GB of RAM and understood that they were more than enough for myth... then you have 16 GB and can record 6 programs. Maybe I can find some use for an extra 2 GB of RAM I have laying around...

---

### Post by ian dobson on 2011-05-25
> **dibuntux said:**
> Very interesting. I think I've always used partitions to setup RAID with mdadm. Infact I never used the mdadm directly but by means of ubuntu installation or Disk Utility, and I think they both use partitions.

I've only 2 GB of RAM and understood that they were more than enough for myth... then you have 16 GB and can record 6 programs. Maybe I can find some use for an extra 2 GB of RAM I have laying around...

With so much ram/a UPS the write cache can get quite large without having to touch the disk. I also have 4 2tb drives in a RAID5 array and a quick quad core CPU (far too much for a MythTV system) but I use the box for other work and myth is only a small job on it.

I've put together a mythtv box for a friend, using an old 2GHz AMD box, 2Gb ram and a 500Gb harddisk. That was enough for recording 2 programs and watching a third on the same box.

Regards
Ian Dobson

---

### Post by dibuntux on 2011-05-27
OK. I would like to make best use of my strange disks scheme, so I'm at it again.

I now managed to install Ubuntu on RAID1 using the 1.5 TB & 2 TB disks. I now have 2 md device, 1 for / of 20 GB and 1 for swap of 1 GB. Using the BIOS disk boot priority I can select which installation can start the PC: The standard Mythbuntu with my partial backup & data that I use to watch TV, that starts from the 500 GB disk and one new Ubuntu that starts from RAID1 device. All videos and recording are on a separate ext4 partition.

What I would like to do is:
1) backup the system structure from / of the 500 GB disk with Mythbuntu and restore it on the / of the new Ubuntu partition on RAID1
2) I should now have a transformed Ubuntu-> Mythbuntu system that works like the original, but from a RAID1.
3) Point all Storage groups to the separate ext4 partition and verify that the system works.
4) Erase the 500 GB disk and create on it 2 RAID1 partitions of 20 GB and 1 GB to add as spare to the already running RAID1.
5) use the remaining 475 GB space on the 500 GB disk to create a new RAID5 with almost 1 TB of redundant storage using all 3 disks. 
6) find a use for the remaining 1 TB and 1.5 TB partitions on the big disks.

Potential problems? TIA

---

### Post by nickrout on 2011-05-28
Problems? over complexity!!

I don't see why you need raid1. A working mythtv system is recreatable in about an hour from bare metal plus the database backup and (naturally) having your data on a separate disk.

What i would do?

1. Backup your database.

2. Install mythbuntu to 500 G disk, / needs maybe 20-50G.

3. Use the balance of the 500G disk and the 1.5T and 2T as storage group for videos and recordings.

I can record 4 or 5 streams and play back to two frontends with a pretty basic motherboard/sata disk combination. No raid. 

BTW the output of your fdisk may be lying, mine says 512b blocks, but I know it has 4k blocks. depends how old your fdisk is.

Take a look at the label on the disk. Thet usually have a warning if they have 4k blocksize.

---

### Post by dibuntux on 2011-05-28
Nick, there is wisdom in your words. Why RAID? Becouse I can, I guess... I'm a geek. Seriously, I liked the idea of a fault tolerant system on my media too. But maybe I'm just unnecessary complicating my life.
Right now the system is on the 500 GB and working, with other disks for medias on Storage groups for load balancing.

As for the fdisk, it is the latest mythbuntu 10.04 upgrade, so I think pretty recent. No warning label of 4k on the 2 TB disk.

I'll let you know. Thanks!

---

