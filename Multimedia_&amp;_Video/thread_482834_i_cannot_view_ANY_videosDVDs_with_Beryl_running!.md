---
title: "i cannot view ANY videos/DVDs with Beryl running!"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by CC_machine on 2007-06-24
OK, so i installed Ubuntu on my new dell inspiron 6400. Whopee, everything works! :D
specs:
1.73ghz intel core 2 duo
1gb 533mhz ddr2 ram
120gb harddrive (10gb fat32, 22gb ext3, 88gb NTFS)
intel media accelerator 950  (though in BIOS it identifies as a 945G)
running at 1280x800 native with 915resolution from synaptic

my problems are:
1. i have a few DVDs that refuse to play properly (without beryl), but i dont mind this much
2. my main problem is that VLC, ogle and all my media players always crash when Beryl is on when trying to play a video or DVD! i can play mp3s okay... I should be abe to show that beryl works with live video previews etc though :(... any suggestions?


heres what happens when i try ogle:
[B]ccmachine@CCsMachine-IV-portable:~$ ogle

*** libdvdread: CHECK_VALUE failed in ifo_read.c:453 ***
*** for vmgi_mat->first_play_pgc < vmgi_mat->vmgi_last_byte ***

xscreensaver-command not found.
WARNING[ogle_mpeg_vs]: B-frame before forward ref frame
WARNING[ogle_mpeg_vs]: B-frame before forward ref frame
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  65
  Current serial number in output stream:  65
ccmachine@CCsMachine-IV-portable:~$ 
[/B]

VLC:
[B]ccmachine@CCsMachine-IV-portable:~$ vlc
VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: SHAUN_OF_THE_DEAD
libdvdnav: DVD Serial Number: 317c01fd
libdvdnav: DVD Title (Alternative): SHAUN_OF_THE_DEAD
libdvdnav: Unable to find map file '/home/ccmachine/.dvdnav/SHAUN_OF_THE_DEAD.map'

*** libdvdread: CHECK_VALUE failed in ifo_read.c:345 ***
*** for vmgi_mat->first_play_pgc < vmgi_mat->vmgi_last_byte ***

libdvdnav: DVD disk reports itself with Region mask 0x00bd0000. Regions: 2 7

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000158
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000de91
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00020d5d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00235fd0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002b5780
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002ee873
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003ce677
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x003cfb8f
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  85
  Current serial number in output stream:  86
ccmachine@CCsMachine-IV-portable:~$ 
[/B]

Video driver: xserver-xorg-video-intel from synaptic, i have "intel" as the driver in my xorg.conf.
note: i can pay *youtube* videos at least :) but they are low quality :(

---

### Post by kvelarde on 2007-07-11
I'm no expert on this but when I tried to use the xserver-xorg-video-intel driver on my Inspiron 6000 laptop, I had the same problem. I had been using the i810 driver with my onboard i915 chip and everything works great. I can watch videos with Beryl running but had the same problem as you when I tried the intel driver. I wanted to switch so I could use the full 1920x1200 resolution that I have with Windoze.

Not sure if the i810 dirver will work with your video card but it might be worth a shot.

---

