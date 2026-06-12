---
title: "DVD Playback in...anything?"
date: 2006-11-13
forum: Multimedia &amp; Video
---

### Post by the ev on 2006-11-13
I've been scouring the Ubuntu forums and haven't come across any fixes for this...

I can't seem to play legit DVDs (that I bought) in Ubuntu 6.10 Edgy Eft using any program.  I've tried Totem, VLC, Mplayer, Xine, and Ogle, and none seem to be able to open the DVD.  And I've tried with several discs, so I know it's not the disc.

Running from the terminal, VLC gives me this when I try to open a DVD:
```
VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.9 from http://dvd.sf.net
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: HUNT_FOR_RED_OCTOBER
libdvdnav: DVD Serial Number: 2E467B0A
libdvdnav: DVD Title (Alternative): HUNT_FOR_RED_OCTOBER
libdvdnav: Unable to find map file '/home/evan/.dvdnav/HUNT_FOR_RED_OCTOBER.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
*** Zero check failed in ifo_read.c:926
    for vts_ptt_srpt->zero_1 = 0x4427

*** libdvdread: CHECK_VALUE failed in ifo_read.c:928 ***
*** for vts_ptt_srpt->nr_of_srpts < 100 ***

libdvdnav: ifoRead_VTS_PTT_SRPT failed - CRASHING!!!
vlc: vm.c:203: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)

```

Now, I was able to decode some of this, and I found similar posts about having libdvdcss installed on my system - which I do and it is up to date (libdvdread3).

Trying to play the disc with Ogle yeilds the following:
```
WARNING[dvd_gui]: add_keybinding(): No such action: 'SaveScreenshot'
WARNING[dvd_gui]: add_keybinding(): No such action: 'SaveScreenshotWithSPU'
*** Zero check failed in ifo_read.c:1060
    for vts_ptt_srpt->zero_1 = 0xc012

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1062 ***
*** for vts_ptt_srpt->nr_of_srpts < 100 ***

FATAL[ogle_nav]: ifoRead_VTS_PTT_SRPT failed

```

I found a suggestion elsewhere on the forum that said to try running ogle with a target.  ogle /media/cdrom1 (my mount point for the disc) spews out many lines of code, all roughly looking like 
```
*** libdvdread: CHECK_VALUE failed in ifo_read.c:1144 ***
*** for vts_ptt_srpt->title[i].ptt[j].pgn != 0 ***

```
before it terminates to
```
FATAL[ogle_nav]: ifoRead_PGCI_UT failed

```

Totem:
```
Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.
```

And Mplayer:
```
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU:              Intel(R) Pentium(R) D  CPU 2.66GHz (Family: 15, Model: 4, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing dvd:///dev/hdb.
Option stream url: This URL doesn't have a hostname part.
Couldn't open DVD device: /dev/dvd
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  4587.2 kbps (573.4 kbyte/s)
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] This driver only supports the 3Dfx Banshee, Voodoo3 and Voodoo 5.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
V:   0.5   8/  8 ??% ??% ??,?% 0 0 

Exiting... (End of file)

```

With Mplayer, I did the command mplayer dvd:///dev/hdb.  When I do, a window comes up very briefly with the FBI warning screen (you know, the copy warning at the beginning of every DVD), but then closes almost instantly.  I can only get that to happen if I use sudo as well.

When I was looking around online for a fix, I saw that you can normally start a DVD with mplayer and VLC by referring the program to /dev/dvd, but I noticed that my DVDs always seem to mount from /dev/hda or /dev/hdb to /media/cdrom0 or /media/cdrom1.  I don't have an IDE harddrives in this system (all SATA), so could that be screwing things up? That the only things on the IDE channel are optical drives, thus Ubuntu recognizing them as hda and hdb instead of /dev/dvd? 

DVD Ripping programs also seem to not have access to the DVD. dvd::rip can't scan TOC from the selected drive (either of them - I have two DVD drives), either spitting out and error message:
```
Job 'Read TOC (lsdvd)' failed with error message:
Error reading table of contents. Please check your DVD device settings in the Preferences and don't forget to put a DVD in the drive.
```
...or hanging until the program crashes.  AcidRip is no better: it defaults to /dev/dvd and, of course, finds nothing.  If I manually type in /dev/hdb or /dev/hda (depending on which drive I put the DVD in), I'm still greeted with
```
Can't read DVD track. Faulty Disc?
```
Now I know these discs aren't faulty, since they play fine on any Windows system, and they played fine on OpenSUSE 10.1, which I had installed before switching to Ubuntu.  I also am unable to dumb VOBs from mplayer.

I don't know if it makes much of a difference, but I'm running the latest BETA drivers from Nvidia (I don't know the version, but I had to find a special tutorial to get Beryl running).  Also, my distro is x86_64 (64bit processor) - would that make a difference?

Apologies about the length of the post; I'm in the twilight zone of knowing enough about these sorts of things and not knowing enough, so I've a skewed sense of what information is relevant and what isn't, though I know that more is generally better.  I feel like I might be missing something simple, but I haven't been able to find help anywhere else.

I'm open to any and all suggestions! Thanks in advance for your time!

---

### Post by Jagot on 2006-11-13
Have you followed this:

[https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

---

### Post by the ev on 2006-11-13
I followed those instructions and VLC still instantly quits when trying to open up a DVD.

```
VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.9 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdnav: DVD Title: HUNT_FOR_RED_OCTOBER
libdvdnav: DVD Serial Number: 2E467B0A
libdvdnav: DVD Title (Alternative): HUNT_FOR_RED_OCTOBER
libdvdnav: Unable to find map file '/home/evan/.dvdnav/HUNT_FOR_RED_OCTOBER.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00006c70
libdvdread: Elapsed time 2
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00006ec8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00006f4b
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00006f69
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x000905cf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00098e58
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x000aa4bf
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003efa16
libdvdread: Elapsed time 0
libdvdread: Found 5 VTS's
libdvdread: Elapsed time 3
libdvdnav: Suspected RCE Region Protection!!!
*** Zero check failed in ifo_read.c:926
    for vts_ptt_srpt->zero_1 = 0x7819

*** libdvdread: CHECK_VALUE failed in ifo_read.c:928 ***
*** for vts_ptt_srpt->nr_of_srpts < 100 ***

libdvdnav: ifoRead_VTS_PTT_SRPT failed - CRASHING!!!
vlc: vm.c:203: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)
```

Ogle gives me the same errors as previously posted, and mplayer behaves the same way with the exception that the video window with the FBI warning stays up for maybe 3 seconds longer before automatically closing.

```
evan@evan-desktop:~$ mplayer dvd:///dev/hdb
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU:              Intel(R) Pentium(R) D  CPU 2.66GHz (Family: 15, Model: 4, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing dvd:///dev/hdb.
Option stream url: This URL doesn't have a hostname part.
Couldn't open DVD device: /dev/dvd
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  4587.2 kbps (573.4 kbyte/s)
open: No such file or directory
Couldn't open: /dev/mga_vid
open: No such file or directory
Couldn't open: /dev/mga_vid
[VO_TDFXFB] This driver only supports the 3Dfx Banshee, Voodoo3 and Voodoo 5.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
V:   0.5   8/  8 ??% ??% ??,?% 0 0 

Exiting... (End of file)

```

Any other suggestions?

---

### Post by the ev on 2006-11-15
In frustration, I installed Ubuntu 6.10 i386 on another hard drive and tried to get DVD playback working on that (rather than x86_64) and after wrestling with libdvdcss2, I got perfect playback.  

?!?

I'm guessing that my problem described earlier is a x86_64 related problem?  Anyone care to comment? :confused:

---

### Post by daveyiv on 2006-11-22
anyone figure this out for x86_64 mine isn't working either.

---

### Post by power.supply on 2006-11-24
I don't know, but I think its got something to do with having 2 dvd drives. Cause I am running a 32bit p4 and still having the same problems as you guys. I don't know if it is a problem but shouldn't dvd drives mount as dvd0 and dvd1. Not cdrom0 and cdrom1? Looking in the forums heaps of people have had the same problem with different apps but no success. All have had multiple dvd drives.

---

### Post by coln_panic on 2007-01-13
for what it's worth, i am having a very similar problem w/ AMD athlon 2500+ system running 6.10 i386 with 1 dvdrw drive and 1 cdrw.  anyone find a solution other than reinstalling?  i know i used to have it working, but have since reinstalled and didn't use my dvd drive for a long time.  all error messages mention something about libdvdread, so maybe somehow getting a different version?  i may try to unplug the cdrw drive to check if multiple optical drives causes the issue, but it doesn't seem too likely (although stranger things have happened...)

jay

---

### Post by Hub-1 on 2007-01-13
It probably doesn't help. Delete .dvdcss and try again.
```
rm -r ~/.dvdcss
```

---

### Post by coln_panic on 2007-01-13
of course, i spoke too soon... following the link posted above, and then the link for DVD playback, i ran this command:
```
sudo  /usr/share/doc/libdvdread3/install-css.sh
``` which fixed all my problems with dvd playback and running dvdrip.  i guess it pays to read the help docs sometimes - although why you have to manually run that is beyond me... :rolleyes:  

jay

---

### Post by BoBr on 2007-01-17
Similar problems, with resolution as in the previous post, only in my case I found the script in a subdirectory of libdvdread3. In particular, my command was (I am running Kubuntu 6.06):
```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```
Before executing the script, I couldn't play any of the legitimate DVDs I had.

---

### Post by BatteryCell on 2007-02-16
Yea Im on x86_64 and am having similar problems, the thing is that some dvds work but some don't.  So like playing/ripping LOTR2 works but not LOTR3 and such. The install css script actually downgrades the libdvdcss I have so I'm not to inclined to do it.

Does anybody know if this is a specifically a 64 bit problem, or just one in general?

---

### Post by Prometheus28 on 2007-12-25
> **coln_panic said:**
> of course, i spoke too soon... following the link posted above, and then the link for DVD playback, i ran this command:
```
sudo  /usr/share/doc/libdvdread3/install-css.sh
``` which fixed all my problems with dvd playback and running dvdrip.  i guess it pays to read the help docs sometimes - although why you have to manually run that is beyond me... :rolleyes:  

jay


It took me four days to figure out this was the problem with k9copy. Four days. Please developers fix this bug IMMEDIATELY.

---

