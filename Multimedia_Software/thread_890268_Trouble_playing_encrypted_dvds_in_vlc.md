---
title: "Trouble playing encrypted dvds in vlc"
date: 2008-08-14
forum: Multimedia Software
---

### Post by misshannah on 2008-08-14
I'm trying to play an encrypted dvd in vlc, this is what it reads in the terminal when I try to run the disk:

han@han-laptop:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: Pilates Band
libdvdnav: DVD Serial Number: c31b004f        
libdvdnav: DVD Title (Alternative): Pilates Band
libdvdnav: Unable to find map file '/home/han/.dvdnav/Pilates Band.map'
libdvdnav: DVD disk reports itself with Region mask 0x00400000. Regions: 1 2 3 4 5 6 8
[00000283] main playlist: nothing to play

Reading through other posts I saw that the problem might be that I didn't have libdvdcss2 installed, so I did that and the DVD still won't play.

Any ideas??

---

### Post by mc4man on 2008-08-14
Try going to home directory -> view -> show hidden files, and find the .dvdcss folder. Open it up and shift+delete all the folders inside. Then give it another try.
If not post another terminal output from vlc

---

### Post by goneboy87 on 2008-08-15
While you should look into the legality of installing libdvdcss2 in your area, this is the additional item to install for your problem.  If you haven't already installed it, install libdvdread3 using synaptic.  Because of the legal questions of libdvdcss2, which decrypts the dvds, it is not automatically installed.

Go to /usr/share/doc/libdvdread3 and run the script install-css.sh

This should solve it for you.

---

### Post by Murdoc_of_puts on 2008-08-16
I tried the libdvdread3/install-css.sh , to no avail.  I also tried the ->/doc/kaffeine/install-css.sh with the same results : encoded dvd.  I also tried looking for the hidden dvdcss file in the home directory, but couldn't find it. What else can I do?

---

### Post by Murdoc_of_puts on 2008-08-16
here is the terminal output:

murdoc@puts:~$ kaffeine
murdoc@puts:~$ libdvdnav: Using dvdnav version 1.1.11.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Attempting to use device /dev/sda1 mounted on / for CSS authentication
libdvdread: Could not open /dev/sda1 with libdvdcss.
libdvdread: Can't open /dev/sda1 for reading
libdvdread: Device /dev/sda1 inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/murdoc/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdnav: Using dvdnav version 1.1.11.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: vm: faild to open/read the DVD

---

### Post by mc4man on 2008-08-16
@ Murdoc_of_puts
> libdvdread: Attempting to use device /dev/sda1 It's doubtful sda1 is your dvd drive 
run ```
sudo lshw -C disk
``` to get device and /dev links for your dvd drive and adjust in kaffeine's settings as needed

---

### Post by Murdoc_of_puts on 2008-08-21
This is the read out for  sudo lshw -C disk: 
description: DVD reader
       product: DVD-ROM DVD-115
       vendor: PIONEER
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1.11
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=open
I tried to change the dvd device in the engine>media parameters to all of the /dev items listed above, and it is still looking to sda1(harddrive partition) first, with a failure opening the /dev/*above* with libdvdcss.  Is there somewhere else that I might change it?  Or is my computer set up wrong? It will however play a vcd with no problems.

---

### Post by mc4man on 2008-08-21
You didn't say if your using kubuntu or ubuntu (8.04 , 7.10 ?)
I don't use kubuntu much or kaffeine at all but as I remember the dvd device in xine parameters should be /dev/scd[COLOR="Red"]x[/COLOR]. Using /dev/dvd or /dev/dvd1 doesn't work too well. I'd try that again after confirming the scd[COLOR="Red"]x[/COLOR] of your drive.
Maybe look in fstab, > cat /etc/fstab

and for interest's sake  see what's shown here (use maximized terminal for readability

>  cat /etc/udev/rules.d/70-persistent-cd.rules


---

### Post by misshannah on 2008-08-25
Tried deleting those files and the dvd still won't play. Here's the terminal output this time around:

han@han-laptop:~$ vlc
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: Pilates Band
libdvdnav: DVD Serial Number: c31b004f        
libdvdnav: DVD Title (Alternative): Pilates Band
libdvdnav: Unable to find map file '/home/han/.dvdnav/Pilates Band.map'
libdvdnav: DVD disk reports itself with Region mask 0x00400000. Regions: 1 2 3 4 5 6 8
libdvdread: Can't allocate memory for file read!
libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:218: ifoOpenNewVTSI: Assertion `0' failed.
Aborted

---

### Post by Murdoc_of_puts on 2008-08-28
I'm using xubuntu with kde installed.  I tried changing it to the sdc, and it still didn't work. Here is the read out for the persistent rules command.


# DVD-ROM_DVD-115 (pci-0000:00:04.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-scsi-1:0:1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-scsi-1:0:1:0", SYMLINK+="dvd", ENV{GENERATED}="1"
# 52MAXX_3252AJ1 (pci-0000:00:04.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-scsi-1:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-scsi-1:0:0:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"

---

### Post by mc4man on 2008-08-28
> I'm using xubuntu with kde installed That's a combo I'm not too familiar with. ( I'm fairly sure if you weren't using kde you'd have been watching movies a long time ago

What I just did see on a recent kubuntu install was commercial dvd's initially not being handled properly by default.
 
Basically while the dvd disk would be recognized and would show up on the desktop, it (the file system) wasn't mounted. Unfortunately the only r.click options are unmount or eject. (vs. a few months ago when you could go r. click -> mount (turn on the green light 
**Any** attempt to get kaffeine or vlc to open the disk would fail.

What worked was to **one time** open the disk in the file manager, right click on the VIDEO_TS folder - open with kaffeine. That actually mounted the file system and ever since then, when i insert a comm. dvd, it's properly mounted, playable and accessible from the mount point and or device node (/dev/scd0 in my case

I guess kde needed a little 'hand holding' (or i need to upgrade configuration skills 

yours is /dev/scd1 ( not sdc, sda or sd anything

---

### Post by exius on 2008-11-11
Hi, 

I have the same problem with not being able to play legal DVDs on Ubuntu 8.04 Hardy Heron using VLC or Movie Player.  It has libdvdcss2 and libdvdread3 installed.  I have followed all those troubleshooting advices posted in this thread, but no luck.  Here's some output:

```
tara@TT-Charged:~$ vlc /dev/dvd
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: CHOCOLAT
libdvdnav: DVD Serial Number: 2a9aa508
libdvdnav: DVD Title (Alternative): CHOCOLAT
libdvdnav: Unable to find map file '/home/tara/.dvdnav/CHOCOLAT.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000014e3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00001667
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x001d7779
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001d94be
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1522 ***
*** for info_length % sizeof(uint32_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1522 ***
*** for info_length % sizeof(uint32_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1522 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:214: ifoOpenNewVTSI: Assertion `0' failed.
Aborted

```

[COLOR="Sienna"]Any assistance would be nice!  Thanks.[/COLOR]

---

