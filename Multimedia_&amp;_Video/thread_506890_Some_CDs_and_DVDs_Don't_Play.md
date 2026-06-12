---
title: "Some CDs and DVDs Don't Play"
date: 2007-07-22
forum: Multimedia &amp; Video
---

### Post by bigjack on 2007-07-22
I added this to another thread "Can't read all CD's or DVD's" in General Help, but so far have received no response.  I tried everything that was suggested in that thread but still have the following problem.

I used to could play all CDs and DVDs on my IBM ThinkPad T40 with Feisty (Ubuntu or Kubuntu), but in the past month or so some CDs and DVDs do not start.  All I get from the drive are a few clicking sounds.  With the few audio CDs that work, I am able to rip them to mp3 or ogg, whichever I choose.  The DVDs that mount can be viewed.  The CDs and DVDs that don't start will work on another computer (Mac OS-X) and with standard CD/DVD players.

I've checked all help with regards to codecs but nothing has helped.  With Kubuntu, in System Settings=>Advanced=>Disk & File Systems I've tried to enable Optical Disk DV-18E.
Mount point is /media/cdrom0
Type is "auto"
Device is "/dev/scd0"
 "Disabled" 

When one of the CDs that can play is in the drive, and through "Administrator Mode" I try to enable, this is the error message.

An error occured while enabling /media/cdrom0.
The system reported: mount: /dev/scd0: can't read superblock.

If nothing is in the drive or one of the CDs that will not start is in the drive, the error is:
Return code from mount was 32.  "mount failure"

---

### Post by grayhammer on 2007-07-22
Gut feeling tells me that your drive is on it's way out.  How old is the computer?  If the disks are scratched at all, an older drive may have more trouble reading them than a brand new on might.

You might try booting a Feisty Live-CD, if you have one.  If it gives you trouble, it's probably your drive.  Another way to check would be to install a different OS on the machine, and see if it also has trouble.

---

### Post by bigjack on 2007-07-25
The drive works on other computers not running Ubuntu or other forms of Linux.  I suspect that the problem is  related to what I posted in the thread listed below.  But this is beyond me on how to correct the problem.  There have been a lot of problems with CD/DVD drives if anyone does a search for CD/DVD etc.  Anyway, look at what I posted in the other thread.

[http://ubuntuforums.org/showthread.php?t=508728](http://ubuntuforums.org/showthread.php?t=508728)

Any help will be appreciated. Could these threads be combined?

---

### Post by hanzomon4 on 2007-07-25
I'm having the same problems, some cds or dvds just won't show up...

---

### Post by bigjack on 2007-07-29
I don't understand why someone hasn't figured out that this is a real problem with Linux in general.  After doing some more internet searches, I discovered that this problem as been around for several years.  It might have to do with a problem in the kernel itself (see near the end of this post).

I have been using Ubuntu Linux for several years.  Was using 7.04 (Feisty) for about 6 months, but reinstalled 6.10 (Edgy) because for some reason, my IBM ThinkPad T40 runs faster with it.  I also have installed and tried Fedora Core 7, Mandriva, Linspire, and openSUSE 10.2.  All distributions were installed through CDs (i.e., the CD/DVD drive works when not accessed through Linux).  For the IBM ThinkPad T40, Ubuntu 6.10 (Edgy) appears to be the best overall.

There is a problem with Edgy as well as with Feisty and the other Linux distributions I have tried:  The CD/DVD ROM does not work consistently--many CDs and DVDs do not open.  All that happens is a click click coming from the CD/DVD-ROM drive.  The problem is not codecs:  All codecs for playing DVDs and CDs have been added from the various repositories.

When I check hdparm with "sudo hdparm /dev/hdc" the result is:

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

In Feisty, hcd was replaced by scd0, but results were the same.

When I searched various Linux forums for help with the "Inappropriate ioctl . . ." problem, I was able to see that others have had the problem, but that no forum directly answered how to fix the problem.  I came across the cdrom.h file through a search for commands in Unix, not Linux.

What can be done to correct this problem?
HDIO_GETGEO failed: Inappropriate ioctl for device

It possibly has to due with cdrom.h in the kernel.

/usr/src/linux-headers-2.6.17-10-generic/include/linux/cdrom.h
/usr/src/linux-headers-2.6.17-10-generic/include/config/sc6600/cdrom.h
/usr/src/linux-headers-2.6.17-10/include/linux/cdrom.h
/usr/src/linux-headers-2.6.17-12-generic/include/linux/cdrom.h
/usr/src/linux-headers-2.6.17-12-generic/include/config/sc6600/cdrom.h
/usr/src/linux-headers-2.6.17-12/include/linux/cdrom.h

I am a novice to computer programming but can follow clear and concise directions.  Anyone out there know how to modify cdrom.h so that CD/DVD ROMS (and possibly burners) work?

I'm going to add this to the other thread listed in a previous contribution to this thread.  These threads should be combined and someone who knows something about cdrom.h contribute to solving the problem.

---

### Post by daverave999 on 2007-07-30
I am also unable to mount optical media. I'm pretty convinced it's not my hardware seeing as it has only happened recently, seemingly the same time as this happening to several other people. Broken by an update?

---

