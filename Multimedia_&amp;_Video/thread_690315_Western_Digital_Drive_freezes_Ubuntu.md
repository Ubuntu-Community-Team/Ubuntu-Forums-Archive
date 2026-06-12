---
title: "Western Digital Drive freezes Ubuntu"
date: 2008-02-07
forum: Multimedia &amp; Video
---

### Post by saif on 2008-02-07
Hello,

I am having some problems with my USB2.0 WD MyBook hard drive, it has one partition XFS, I have set it to ne mounted to /home in fstab, If the computer is completly shutdown, the drive doesn't get mounted on boot, I have to mount it manually. but If i reboot, it gets mounted. this is the first minor problem I am having which I can live with since I don't shutdown the machine that often.

The real problem is that my gutsi x64 installation keeps crashing at random times (one way to get it to crash for sure is trying to sync with unison over ssh)! everything freezes, no caps lock, no num lock change, cannot ssh to the machine, apache stops responding! I though i had no way of troubleshooting this, on the ubuntu-uk mailing list some1 suggested that it's a hardware problem. so i unplugged the WD hd and tried it without it, and it doesn't crash anymore. so it's definitly a hard drive problem, and I have no idea how to fix it and i definitly need it fixed!

I always thought that the log messages are cleared after a crash like that, but I was told /var/log/messages holds the data, attached is mine after a crash (and rebooting).

Peace,
Seif A.

---

### Post by tgalati4 on 2008-02-07
It looks like a subtle 64-bit, NFS, XFS, external drive problem.  You have 7 partitions on the drive (4 primary and 3 logical).  You are running NFS and not fusesmb.  You have one partition with XFS.  This may be a buggy combination.

Do you have any NTFS partions mounted on this machine?  If so, comment them out in fstab and see if the behavior changes.

Try using fusesmb to mount your external drive and see if the behavior changes.  If NFS balls up, it can take the kernel with it.  Fuse is a user-space file system, which is supposed to be more robust with its interaction with the kernel.

---

### Post by saif on 2008-02-07
Thanks for the quick reply, yeah I do have a lot of partitions, but the external drive is connected via USB and only one XFS partition, this is my fstab.

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ad26f6f9-61ae-414d-8bc3-ec484a74b50d /               xfs     defaults        0       1
# /dev/sda5
UUID=f4d368a2-3c04-4fba-82e3-4adb2dae4ccf /backup         xfs     defaults        0       2
# /dev/sda7
UUID=373cc5ca-0cd2-412e-ac55-bdcfaecde6a5 /boot           ext3    defaults        0       2
# /dev/sda1
UUID=92303AA4303A8EEB /media/ntfs     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=ed5cd76f-0335-4232-9ddc-f1e6a29527fa none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
# /dev/sdb1
UUID=5c896b21-1062-4c9e-b0c0-54604b4b2413 /home           xfs     defaults        0       0



I do have one ntfs partition as you can see, I will try to uncomment it and re connect the WD when I get home. I ad never heard of fusemb before! :) and i always thought that NFS is for network file sharing, so I don't really understand how I am using it for this drive (connected via USB), anyways, thanks for the advice, I will do some reading on fusemb and try it out.

---

### Post by saif on 2008-02-10
Hello,

I removed the ntfs drive from fstab, but sdb1 still crashes, as for fuse, I guess you meant fuse fs? not fusesmb? 
 I want the drive (sdb1 - xfs) to be mounted at boot as /home, I couldn't find any clues on how to tell ubuntu to use fuse to mount the drive. most of the results I got are about using fuse to mount remote locations. or using fuse so that a user can mount a location without root privileges. if you can provide me with any links it would appreciated.

---

### Post by saif on 2008-02-18
ok, It's not working, I have removed the usb drive from fstab and also removed the ntfs, it now only ontains internal drives. and I am assuming the external drive is being mounted using fuse, since i am mounting it with a normal user.

The problem is still there, it always crashes, I am trying to copy the files from the external hard drive to a safe location, and during the copy ubuntu crashes and stops responding, when i reboot /var/log/messages doesnt have anything. I am assuming this is a hardware fdault. but still even if there is a hardware fault, it should not being the whole system down! I have no idea how to troubleshoot or find out what the problem is! the hard drive is still new, but I need to make sure it's a hard drive problem before claiming anything on the warranty. could it be an ubuntu 64 with usb xfs partitions (I tried the same hard drive with another gutsy 64 machine, that crashed as well) ? I dont know, but I do believe this is a bug! it's an external drive, with no data that has anything to do with the system, i dont see why an I/O error crashes the system.

I also noticed that this thread is in the multimedia and video section,i dont know how i managed to do that, nor how to move it to the hardware thread. sorry! :)

---

