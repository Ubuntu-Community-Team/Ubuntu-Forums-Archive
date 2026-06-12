---
title: "Audio-CD not recognised, data CD and DVD video are (same drive)"
date: 2009-12-20
forum: Multimedia Software
---

### Post by javine on 2009-12-20
Hello,

I have a CD/DVD combi drive in my Ubuntu box (9.10). The short version is that video DVDs are automatically picked up when inserted, but audio CDs are not.

I checked out another thread from someone with similar problems, which suggested this might be a hardware problem affecting the CD laser:

[http://ubuntuforums.org/showthread.php?p=8103878](http://ubuntuforums.org/showthread.php?p=8103878)

However, I think I have excluded that as a possibility for my drive - data CDs work fine in the drive.

I have tried several CDs - all official and shop bought - with no success.

I'm pretty new to this, so I'm just mindlessly copying the commands in the previous thread in case they provide some diagnostic information that might help.

fstab:

```
 cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=454802e2-9150-48fd-8a57-206df4e73be9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=947266f4-937e-4b3e-b968-cf3b89f2bd0c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

udev

```
jim@Mr-Smith:~$ cd /etc/udev/rules.d
jim@Mr-Smith:/etc/udev/rules.d$ cat 70-persistent-cd.rules
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
#  (pci-0000:00:1f.1-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
# Flash_Disk (pci-0000:00:1d.7-usb-0:4.2:1.0-scsi-0:0:0:1)
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="CBM_Flash_Disk_11112800C055EA10-0:1", SYMLINK+="cdrom1", ENV{GENERATED}="1"
# Flash_Disk (pci-0000:00:1d.7-usb-0:4.2:1.0-scsi-0:0:0:1)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1d.7-usb-0:4.2:1.0-scsi-0:0:0:1", SYMLINK+="cdrom2", ENV{GENERATED}="1"

```

lshw with no disk in drive:

```
 sudo lshw -c disk
  *-cdrom                 
       description: DVD reader
       product: CDW/DVD TS-H492A
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: TB03
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc

```

Same command with an audio CD in drive:

```
 sudo lshw -c disk
  *-cdrom                 
       description: DVD reader
       product: CDW/DVD TS-H492A
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: TB03
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=busy

```

(After a few seconds the status does revert to "nodisc".)

And with a data CD:

```
 sudo lshw -c disk
  *-cdrom                 
       description: DVD reader
       product: CDW/DVD TS-H492A
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: TB03
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

```

mount:

```
sudo mount /media/cdrom/
mount: no medium found on /dev/sr0

```

ls -al sr0:

```
/dev$ ls -al sr0
brw-rw----+ 1 root cdrom 11, 0 2009-12-20 11:27 sr0

```

uname:

```
uname -a
Linux Mr-Smith 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux

```

Thanks in advance for any help. Hopefully some of those diagnostic outputs will means something to somebody, but let me know if there's any other commands I could usefully run.

Thanks,
Jim

---

### Post by snapback77 on 2010-02-21
I had the same problem.  It was not solved until I disconnected my DVDrom drive.  Then the DVDburner played/recorded both DVD and CD.  Figure?

---

### Post by bart.vanaudenhove on 2010-05-01
I had a similar problem on my HP Laptop: any data cd or DVD would read  and write fine, but audio cds and movie dvds would not be recognized.

For me the solution was to physically slip the optical drive out of the  computer (unscrew a vise in the back and push the drive a bit out) =  unplugged and power off off course =, plug it back in, and at next  startup everything was fine. (I found it in another post somewhere)

From time to time the same problem reappears and the same solutions  works for a while...

This is in Ubuntu 9.10.

---

### Post by MentatGhola on 2011-12-01
I have this problem and I think its why the disk autorun isn't working anymore either.  

I don't think I can remove my cdrom from my laptop, at least not easily.  Acer aspire.  Not sure what else to try.

---

### Post by efflandt on 2011-12-01
Just a note, you cannot **mount** a regular music CD (it does not have computer a file system).  If you have a music CD inserted and open a player can you play the CD?

Do you have **ubuntu-restricted-extras** installed (I assume so if you can play DVD)?

---

### Post by MentatGhola on 2011-12-02
No on my laptop I don't have libdvdcss installed.  

When I insert an audio cd into the drive it appears for a moment in the file manager before it disappears.

VLC wont play the tracks when i run from the track file and I get an error message saying there is a log but I cant seem to find it.  If I go to open a disk from a file in the vlc menu there is nothing to choose since the file manager can't see the disk.  If I manually tell it to open /dev/cdrom then vlc starts playing the tracks and recognizes the track titles even. 

Amarok wont play them either from the file and from inside amarok i can see the cdrom from the "places" tab and I can see track titles etc. but the tracks wont play and i cant add them to a playlist.

---

### Post by MentatGhola on 2011-12-02
[http://ubuntuforums.org/showthread.php?t=1586927](http://ubuntuforums.org/showthread.php?t=1586927)

Link to a related thread dealing with banshee crashes where I have posted this problem.  I should emphasize that i think this is a banshee problem.

---

