---
title: "DVD does not mount (works fine in Windows)"
date: 2008-12-15
forum: Multimedia Software
---

### Post by Izkata on 2008-12-15
This DVD has over 4 GB of data on it split in 350 MB video files.

This problem has existed apparently for years:

August 2008:  [http://ubuntuforums.org/showthread.php?t=884405](http://ubuntuforums.org/showthread.php?t=884405)
July 2006:  [http://ubuntuforums.org/showthread.php?t=218208](http://ubuntuforums.org/showthread.php?t=218208)

I get the exact same output as the post from 2006:

> 
izkata@Izein:~$ sudo mount -t iso9660 /dev/scd0 /media/cdrom0/
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

And this line gets added to dmesg:
[ 3031.037398] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16


Does anyone know anything about this?  As the topic says, this DVD works fine in Windows, no problems.

---

### Post by ajgreeny on 2008-12-15
What exactly do you want to do with this DVD, read the files on it, or is it a  DVD of video you want to play, you don't make it very clear?  Also is this a problem with just this DVD or all others as well?

Does the DVD actually have an iso file on it?  Normally you only use the command you showed when you want to mount (ie. almost the equivalent of unpack) an iso file which is on a CD or DVD, or mount an iso file on your hard disk.  If the iso file is on a DVD try using ```
sudo mount -t iso9660 /media/cdrom0/path/to/iso/file mountpoint
```  that's if it does not automount, which CDs and DVDs do on my setup.  I think you may be trying to mount a device name which is already mounted, perhaps, or have I completely misunderstood your problem?

---

### Post by Izkata on 2008-12-15
This is a physical DVD, not an ISO.  A data disk, with video files that I want to read.

The problem exists with all my DVDs that are nearly full that I have tried.

I am using the terminal because I use WMII; the program that automounts in Gnome, KDE, etc, is not running.  (Opening Nautilus would do it, as it works for CDs and flash drives, but I already tried that - nothing happens with these DVDs)

---

### Post by randallecook on 2008-12-28
I am having the same problem. I put a commercial (US market) movie DVD in the drive, and it's like it isn't there. Running 'sudo mount /dev/dvd' complains that no medium is found. Any suggestions, anyone?

I am trying to decrypt the VOBs to my local hard disk so I can test some video analysis software I am working on with MPEG-2 files. It is important that the content *not* be transcoded.

Randall

---

### Post by albinootje on 2008-12-28
> **randallecook said:**
> I am having the same problem. I put a commercial (US market) movie DVD in the drive, and it's like it isn't there. Running 'sudo mount /dev/dvd' complains that no medium is found. Any suggestions, anyone?

I am trying to decrypt the VOBs to my local hard disk so I can test some video analysis software I am working on with MPEG-2 files. It is important that the content *not* be transcoded.

Randall

You have libdvdcss2 installed, right ?
```

dpkg -l|grep libdvdcss2

```

---

### Post by randallecook on 2008-12-28
Yes. I installed it before I even inserted the first DVD. My system can't even read the DVD files that libdvdcss2 is supposed to work on. It's like I put a round piece of plastic in the drive instead of a $20 DVD. :)

Randall

---

