---
title: "[SOLVED] still no DVD playback."
date: 2008-05-29
forum: Multimedia Software
---

### Post by the badger on 2008-05-29
What I though was originally an issue with K9copy turns out to be a DVD playback issue. I've read as much as I can handle of the many 16-30something page posts on these issues, installed as per the [Comprehensive Multimedia & Video How-to]("http://ubuntuforums.org/showthread.php?t=766683&highlight=can%27t+play+dvd"), added as per the [community docs on DVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs").

Then I found [this post]("http://ubuntuforums.org/showthread.php?t=801771") on changing /dev/dvdrw to /dev/dvdrw1. Only I'm a noob and I've also got a CD-RW drive, so I'm not sure how to proceed with what's posted by mc4man at the handy link above. I'm going to post up my "lshw -C disk" and "70-persistent-cd.rules" and hope like heck somebody can point me in the right direction (instead of erasing the wrong stuff).

[Like everybody else says: I too am running the Heron, clean install, had no playback issues in Gutsy nor Dapper].

lshw:
```

  *-disk                  
       description: ATA Disk
       product: ST380021A
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.1.0
       logical name: /dev/sda
       version: 3.19
       serial: 3HV1FGFC
       size: 74GiB (80GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00000001
  *-cdrom:0
       description: DVD writer
       product: DVD-RW  DVR-112D
       vendor: PIONEER
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.21
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: CD-R/CD-RW writer
       product: CD-Writer+ 8000
       vendor: HP
       physical id: 1
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 2.3C
       serial: [HP      CD-Writer+ 8000 2.3C

```

70-persistent-cd.rules:
```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# CD-Writer+_8000 (pci-0000:00:09.0-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:09.0-scsi-1:0:1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:09.0-scsi-1:0:1:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
# DVD-RW_DVR-112D (pci-0000:00:09.0-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:09.0-scsi-1:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:09.0-scsi-1:0:0:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:09.0-scsi-1:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:09.0-scsi-1:0:0:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"
```

so, should i erase those "1"s?

---

### Post by mc4man on 2008-05-29
> so, should i erase those "1"s?  no, your fine in that regard, that issue doesn't pertain to you.
If dvd's are mounting why don't you open one of your players from the terminal, try playback of a dvd and post the error print out. (vlc is very good for this). 
What was the issue with k9?

---

### Post by the badger on 2008-05-29
Hi there mc4man,
pardon the blatant ignorance, but how to do I ask vlc to play a dvd on the command line? (in the gui it just hangs. it'll auto-launch when i put in a dvd, but it won't do anything and no titles appear).

> What was the issue with k9? 
I think the issue with K9 is whatever is stopping the [commercial] dvds from playing in the first place. the dvd mounts, and in K9 the dvd is loaded, but it won't copy (either to dvd, or to file). it was only when i tried to play a dvd that i realised the problem wasn't so much K9 as, well, everything?

---

### Post by mc4man on 2008-05-30
> vlc to play a dvd on the command line? just open the terminal and type  vlc. Vlc will open , file - > open disc, the default device should /dev/scd0 (if not change to that) click play and see what happens, post errors that show up in terminal.

---

### Post by coolaj86 on 2008-05-30
Try this:
```
wget http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-1_i386.deb
sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```

[http://ubuntuforums.org/showthread.php?t=812406](http://ubuntuforums.org/showthread.php?t=812406)

---

### Post by the badger on 2008-05-30
Amazing(!) but vlc plays the commercial dvd when launched from terminal!?! strange, but it works...
thanks :)

---

### Post by GaussianMonk on 2008-06-04
I too am having a problem playing commercial dvds(Blue Planet series). I tried to run vlc from the terminal and got:
> libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: BLUE_PLANET_DISC1
libdvdnav: DVD Serial Number: 2B8AB762
libdvdnav: DVD Title (Alternative): BLUE_PLANET_DISC1
libdvdnav: Unable to find map file '/home/glen/.dvdnav/BLUE_PLANET_DISC1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
*** Zero check failed in ifo_read.c:1604
    for pgcit->zero_1 = 0xd6b7

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1608 ***
*** for pgcit->nr_of_pgci_srp < 10000 ***

*** Zero check failed in ifo_read.c:648
    for pgc->zero_1 = 0x0001
*** Zero check failed in ifo_read.c:648
    for pgc->zero_1 = 0xb801

*** libdvdread: CHECK_VALUE failed in ifo_read.c:664 ***
*** for pgc->cell_playback_offset == 0 ***

*** Zero check failed in ifo_read.c:648
    for pgc->zero_1 = 0xc001
*** Zero check failed in ifo_read.c:661
    for pgc->still_time = 0xff
*** Zero check failed in ifo_read.c:662
    for pgc->pg_playback_mode = 0xff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:663 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:664 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:665 ***
*** for pgc->cell_position_offset == 0 ***

libdvdnav: ifoRead_PGCIT failed - CRASHING!!!
vlc: vm.c:206: ifoOpenNewVTSI: Assertion `0' failed.

Desperately in need of help here...

---

### Post by mc4man on 2008-06-04
> I too am having a problem playing commercial dvds
> libdvdread: Encrypted DVD support unavailable. go here [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)  add the repo for your ver. of ubuntu, add the GPG key, then either run
```
sudo apt-get install libdvdcss2
``` or install from synaptic.
try again with vlc and if still no good post new errors

---

### Post by GaussianMonk on 2008-06-04
When I run the GPG key code I get:
> E: Type '--23:08:11--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

I assume that is just the time log of when the file was written, so I removed that from line 1 and saved, then tried again. I got:
> E: Type 'http://www.medibuntu.org/sources.list.d/hardy.list' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

---

### Post by GaussianMonk on 2008-06-08
I got it to work by manually adding the Medibuntu repo to my list and updating adept from there. Followed the instructions found [here]("http://ubuntuforums.org/showthread.php?t=766683&highlight=commercial+dvd+playback").

---

