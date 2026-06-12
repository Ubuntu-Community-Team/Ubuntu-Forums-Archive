---
title: "DVD Drive Not Working"
date: 2011-11-21
forum: Multimedia Software
---

### Post by sazawal on 2011-11-21
I am using Ubuntu 10.10 on my Vaio E  series laptop. My CD drive is not working, though I can see a CD/DVD  Drive icon on my Computer. In the System>Administration>Disk  Utility a CD/DVD device appears but it shows "No media inserted". Also  there is nothing in my BIOS options where I can change the mode to HCI  or IDE. I am posting the output of
 $ sudo lshw -C disk
*-cdrom
       description: DVD-RAM writer
       product: DVD RW AD-7700H
       vendor: Optiarc
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.V0
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
 Please help !!

---

### Post by nothingspecial on 2011-11-21
Post moved to it's own thread.

Rather than tagging your problem on to the end of old threads, make a thread of your own in future.

I've done it for you this time.

---

### Post by Acharn on 2011-11-22
I'm having a problem, too, not sure if it's the same. I'm running 11.04, natty narwhal. My result from lshw:

*-cdrom
       description: DVD-RAM writer
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/VIDEOCD
       capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready

My drive is recognizing CD-R's, but when I try to play them with Movie Player I get the message: "An error occurred Could not open location; you might not have permission to open the file." I can see the directory structure in Nautilus, but don't see the video files. I burned these CDs a long time ago and don't remember what extension they had, but they're just not there. However the discs play fine in the VDR attached to my TV set. It does not detect DVDs at all. If I insert a DVD the light comes on and I can hear the drive starting up, but it just runs for five or ten minutes and then stops. With DVDs the drive doesn't even auto mount. I haven't tried mounting it and then reading a DVD.

Following other threads I've installed libreaddvd4, with libdvdcss2. No help. I installed VLC Player. No help. One thing bothers me -- why does the Disk Utility show Connection: SCSI? I've never had a SCSI drive.

---

