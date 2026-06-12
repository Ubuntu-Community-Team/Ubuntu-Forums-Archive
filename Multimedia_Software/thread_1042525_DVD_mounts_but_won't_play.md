---
title: "DVD mounts but won't play"
date: 2009-01-17
forum: Multimedia Software
---

### Post by jpyeck on 2009-01-17
This is my first problem that I haven't been able to research my way to a solution... My thanks to this forum for their previous solutions, and hopefully you'll have some input on this one too!

I recently upgraded my Mythbuntu box from 7.10 thru 8.04 to 8.10.  One strange thing happened... my SCSI DVD drive changed logical name with my second HDD, which messed up my fstab mount points.  Originally I had HDDs at sda and sdb with the DVD drive at something else (I can't remember any more)  Now I have HDDs at sda and sdc and the DVD at sdb.  I was able to fix my fstab to get that working.  My fstab for reference:

> # /dev/sda1
UUID=c419dd00-c140-48ff-9ea8-e321346c815b /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=9af36d5b-804a-4905-8278-d6acefd45ab6 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdc1       /mythdata       ext3    defaults,relatime       0       0


Now my DVD drive will not play DVDs.  I can insert a DVD, see it mounted on the desktop, but not play via MythTV/Xine/VLC.  Xine and VLC give errors about not being able to access the drive at dvd:// (side note, is there a link to dvd:// set somewhere?  It's impossible to google "dvd://" and get relevant results since google ignores punctuation.)  They seem to be defaulting to /dev/scd0 (which I don't have) and I don't have a sym link at /dev/dvd either.

My research so far has had me looking at lshw.  lshw -C disk results here:

>   *-disk:0                
       description: ATA Disk
       product: WDC WD1600AAJS-6
       vendor: Western Digital
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 21.1
       serial: WD-WCAP94108871
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0000dcd8
  *-disk:1
       description: SCSI Disk
       product: DVD-E616A3T
       vendor: ASUS
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 1.10
       size: 7845MiB (8226MB)
       capabilities: removable
       configuration: ansiversion=5
     *-medium
          physical id: 0
          logical name: /dev/sdb
          size: 7845MiB (8226MB)
  *-disk:2
       description: ATA Disk
       product: WDC WD5000AACS-0
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
       version: 05.0
       serial: WD-WCAUF0361501
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=1f547973


I'm concerned that the "capabilities" for my DVD drive show nothing other than "capabilities: removable".  I have read it should be something like "capabilities: removable audio cd-r cd-rw dvd dvd-r".

Is my drive dead/dying or did the SATA-shift mess up some pointers or configuration?

---

### Post by mc4man on 2009-01-18
> Is my drive dead/dying 
No. I'd think your drive is fine.
Actually i can't resist giving this a bit of a bump, never seen a dvd drive detected as a disk drive.

What may be interesting to see is if the drive was ever seen as a cdrom device. When upgrading, the ...cd.rules file isn't redone, just appended to, so if the drive is listed in there it was, at some point, seen as a cdrom and given some /dev links

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

Did you have media in the drive when you ran the lshw? It doesn't indicate a mount point other than possibly /media/disk-1

> I can insert a DVD, see it mounted on the desktop
If you right click on the icon -> properties -> volume, what info does if give? (mount point, mount options, file system

If you were to take the mount point shown and use that in vlc (/media/whatever), can you get playback.

it also may be interesting if you were to comment out the line in fstab, insert a dvd and reboot with the disk in the drive, does anything change in lshw?

---

### Post by jpyeck on 2009-01-18
mc4man, thanks for your reply.  I tried some of your hints... the results are below.

> **mc4man said:**
> 

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```



My ...cd.rules results:

```
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:12.0-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:12.0-scsi-1:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
```

> 
Did you have media in the drive when you ran the lshw? It doesn't indicate a mount point other than possibly /media/disk-1

Yes, I had a "Bourne Identity" DVD in the drive.  

> 
If you right click on the icon -> properties -> volume, what info does if give? (mount point, mount options, file system

I didn't see "volume" info as an option, though at the command line I can see the disk at /media/BOURNE_IDENTITY.

> 
If you were to take the mount point shown and use that in vlc (/media/whatever), can you get playback.

Using /media/BOURNE_IDENTITY in vlc still doesn't work, opened as disk or as directory.

> 
it also may be interesting if you were to comment out the line in fstab, insert a dvd and reboot with the disk in the drive, does anything change in lshw?

I tried this too.  

```

# /dev/sda1
UUID=c419dd00-c140-48ff-9ea8-e321346c815b /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=9af36d5b-804a-4905-8278-d6acefd45ab6 none            swap    sw              0       0
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdc1       /mythdata       ext3    defaults,relatime       0       0

```

The lshw results are below.  Seems the only new thing is the second logical name.

```
  *-disk:1
       description: SCSI Disk
       product: DVD-E616A3T
       vendor: ASUS
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       logical name: /media/BOURNE_IDENTITY
       version: 1.10
       size: 7845MiB (8226MB)
       capabilities: removable
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,uid=1000,utf8 state=mounted
     *-medium
          physical id: 0
          logical name: /dev/sdb
          logical name: /media/BOURNE_IDENTITY
          size: 7845MiB (8226MB)
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,uid=1000,utf8 state=mounted

```

Any more thoughts?

---

### Post by mc4man on 2009-01-18
A couple of observations

As far as the ...cd.rules
A drive was once detected as a cdrom, though certainly not in 8.04 or 8.10 where you would see more info than the 2 lines you show.

Actually your last lshw shows a significant change
Orig.
> physical id: 0
logical name: /dev/sdb
size: 7845MiB (8226MB)
Note no file system and mount shown
Current
> *-medium
          physical id: 0
          logical name: /dev/sdb
          logical name: /media/BOURNE_IDENTITY
          size: 7845MiB (8226MB)
          [COLOR="Blue"]configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,uid=1000,utf8 state=mounted[/COLOR]

This is what you'd expect from dvd media and in this state technically you should be able to access and playback.
You could test this by trying vlc again. Note that playback in vlc 0.9.x is somewhat broken when telling vlc to open a dir.

A more solid test would be to open /media/BOURNE_IDENTITY in a window, open vlc from a terminal, and drag the VIDEO_TS folder onto vlc.


I don't have any setups with a sata dvd drive but I'd think it should be detected as a cdrom device rather than a disk drive. If so, how you force or adjust this I don't know.
It's possible a change in your bios settings is needed but to advise on bios from afar is tricky.

The other possibility is that a fresh install of 8.10 would resolve this.
I see 3 possible outcomes from that:
Everything is good as it should be
You get the same setup as now
Your dvd drive isn't found at all

What I'd be inclined to do is get a live cd of 8.10 and boot up to it. Then ck. ....cd.rules and ..lshw to see how the drive is detected.

---

### Post by trubblemaker on 2009-02-15
Here' a magic incantation I found that got my dvd drive to work
```
 sudo /usr/share/doc/libdvdread3/install-css.sh

```

It's a work around for the legality of commercial encoding of dvd's.... Hope it helps..

---

