---
title: "initramfs exception!"
date: 2007-10-23
forum: Mythbuntu
---

### Post by DwayneWayne on 2007-10-23
I was pleased to see the new version of MythBuntu final!
I went on with installing - instead of using crappy media center. Here my problem occurred. When I try to start from the CD i get this error, just after it has shown the spinning bar upon booting.

```
(initramfs) [ 135.981849] ata3.00: Exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

[135.981911] ata3.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x5a data in

 

[166.437962] ata3.00: Exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

[166.438015] ata3.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x5a data in

 

[196.894084] ata3.00: Exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

[196.894137] ata3.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x5a data in

 

[227.350220] ata3.00: Exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen

[227.350274] ata3.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x5a data in
```

I did test the CD in my desktop computer and it booted and worked good on this machine.

Thanks and best regards to everyone!

---

### Post by superm1 on 2007-10-24
It looks like CD read errors here.  From another machine that you know has a good CD reader, boot the CD and do a "check" from that boot menu.  As long as the CD tests out OK: it sounds like either a dying CD drive, cable, or controller.  If the CD doesn't test out OK, reburn it at slower speed and try again.

---

### Post by DwayneWayne on 2007-10-24
I have already tried what you suggest - the CD is working in my dekstop computer and I also burned the CD at 4x speed.
I think the CD drive is about to die or something similar.

---

### Post by thomaswp on 2007-12-01
Hmmm.

I have the exact same problem.  

On 2CDs.  Burned at slow speed.  By different burners.  In two DVD drives.  

The hash on the iso image is correct.
(d2334dbba7313e9abc8c7c072d2af09c=ubuntu-7.10-desktop-i386.iso)

And when I run vmware using the iso image as the CD...

...I get the exact same problem.

Now I can't imagine that everyone installing 7.10 has had this problem or most likely I would have read it on slashdot.

So what is going on?

---

### Post by merlynx on 2007-12-05
I also have this problem.  I've heard a few theories.  My configuration is older hardware (Dell poweredge 2450, old SCSI backplane, FastTrack 66/100 Fakerraid card on a newer 40gb drive).  WinXP installed fine.

I'm going to test my two CD's (I originally thought I made a shiny coaster) and see if that's the problem.  Whatever I find out, I'll try to remember to post here...

:confused:

---

### Post by merlynx on 2007-12-05
Update:
Well - followed some advice from this guy:
[http://williamtasso.com/tech/poweredge2300.html](http://williamtasso.com/tech/poweredge2300.html)

I did two things:
1 - Turned off my PERC Si and connected the SCSI backplane to the extra "Channel B" adaptec SCSI controller.
2 - Instead of using the Gutsy 7.10 used Dapper 6.06 LTS

I'm installing now on the FastTrack Controller-Card-Managed 40GB drive even as I type this...we'll see if "she go" after these massages.

---

### Post by vt100 on 2007-12-24
My bootup droped to an initramfs prompt and I have a high point 1640 card in my box. I removed it and it booted like magic. Guess the CD didn't like the raid card. On booting up after the install with the card back in it gives me the same initramfs error again. I'm going to try installing the proprietary drivers for the card since it doesn't work with the card even without the drives connected. 

It worked fine in Fedora and Oracle Unbreakable Linux without the drivers just saw the individual drives.....

---

### Post by Efrain Valles on 2007-12-25
I am also trying to install on older more modest hardwre. I am able to install using the ubuntu minimal install. but once installed, I get the same **ata1.00: exception Emask error**. I tried on two different drives

People keep telling me the drives are dead.. I tend to think it's definetely new kernel stuff... why does 2.6.15-26 works and the newer kernels don't. beats me... but this is what I found in launchpad

[URL="https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/146577"]https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/146577
[/URL]

I might just get an new Hard Drive... :S

---

### Post by Efrain Valles on 2007-12-27
Ok... I installed on my old hard Drive... it appears to be some missing modules for old ide hard drives and CD rom units...

here is what I did

I was able to boot livecd.. if you are not able to boot a livecd add some options to the boot parameters in the live cd... 

1) press F6 por boot options... and int he begining of the line add:

**break=top ** 

make sure you leave a space between break=top and the next words in the line (should be something like file://...)

at the end remove the words **quiet** and **splash** and right there add **all-generic-ide**

one you pres enter the cd will try to boot and will fall in the iniramfs prompt... there you type.

```

modprobe ide_generic (press enter)

modprobe ide_disk  (press enter)

modprobe ide_cd (press enter)

exit
```

there you should see the Live CD running...


I installed normally using a live cd. After if finished, I added some extra modules in initramsfs:

here's how:
   since I am in a live cd... and I need to make changes permanent on the actual installed system. I mounted the hard drive partition where /boot is (usually people install on one partition and have swap in another). I used chroot to login into that actual environment as root. and make the change in initramfs...

steps:

#give yourself administrator priviledges
```
sudo -i
```

1) mount your partition:

#first make a directory where you will mount your partition
```
mkdir /mnt/hd
```
#mount your partition in the newly created directory
```
 mount /dev/hda1 /mnt/hd
```

2) log into the installed environment using chroot
```
chroot /mnt/hd /bin/bash
```

3) add the modules to initramfs
```
nano /etc/initramfs-tools/modules
```

you need to add the modules ide_generic  ide_disk and id_cd
so your file should look like this

```
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
ide_generic
ide_disk
ide_cd

```

later update initramfs with the new modules in place...

```
update-initramfs -u
```

after it's done... you can reboot into the installed system...
It has worked fine for me since then...

---

### Post by realtimexxx on 2008-02-08
Thanks.  

I tried initramfs exception!

Everything worked until I got to the mount.  Then I got the message
dev hda1 does not exist

So I just hit enter

The live version came up.
I displayed device information but did not know how to interpret the information.

Not knowing what to do I selected “Install” on the desktop.

I have 3 hard drives
60 GB IBM-Hitachi
20 GB old Maxtor
230 or so SATA drive with Suse 10.3 on it.

During the install I tried to install it on the relatively new 60 GB drive.
It would not install so I tried to install it on the old 20 GB Maxtor 

It worked.  I would like to install it on the 60 GB drive because the 20 GB is old and is likely to fail before the others.  But it is OK for now.

---

