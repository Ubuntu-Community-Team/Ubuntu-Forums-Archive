---
title: "dvd menu support for mplayer"
date: 2011-07-17
forum: Multimedia Software
---

### Post by beew on 2011-07-17
Hi,

I am using mplayer with Umplayer/Smplayer as graphic front ends. I have enabled DVD menus by checking the box in Preference > Drives in Umplayer(also tried Smplayer) but there is still no menu when I stick a DVD in the dvd drive, on the other hand the menus show up if I use VLC to play the DVD so it is not the dvd's problem.

I have already installed libdvdnav4. Any idea? Thanks.

---

### Post by andrew.46 on 2011-07-17
Do you get dvd menu support by running the following from the commandline:

```
mplayer -mouse-movements -nocache dvdnav://
```

---

### Post by SeijiSensei on 2011-07-18
rvm (the SMlayer developer) has a pretty detailed discussion of the menu issue here: [http://smplayer.berlios.de/forums/viewtopic.php?id=743](http://smplayer.berlios.de/forums/viewtopic.php?id=743)

---

### Post by beew on 2011-07-24
> **SeijiSensei said:**
> rvm (the SMlayer developer) has a pretty detailed discussion of the menu issue here: [http://smplayer.berlios.de/forums/viewtopic.php?id=743](http://smplayer.berlios.de/forums/viewtopic.php?id=743)

Hi, tried that, but didn't work. I am actually using mplayer2 with Umpayer,--the relevant options are same as Smplayer. Mplayer2 was compiled with dvdnav support.
In any case it seems rather strange to require own window for mplayer and that seems to screw up the resolution for local files as well.

---

### Post by beew on 2011-07-24
> **andrew.46 said:**
> Do you get dvd menu support by running the following from the commandline:

```
mplayer -mouse-movements -nocache dvdnav://
```

Hi, I am sorry, I am not sure what to do with this as I don't watch videos with command lines, do you put in a dvd and then just type these in the terminal? Do you need to type /dev/dvd or something like that in the end?

---

### Post by andrew.46 on 2011-07-24
> **beew said:**
> Hi, I am sorry, I am not sure what to do with this as I don't watch videos with command lines, do you put in a dvd and then just type these in the terminal? Do you need to type /dev/dvd or something like that in the end?

The commandline given should just open up the dvd menu with no other parameters needed. It is useful to see if there is a problem with MPlayer itself or a problem with the gui used to control it.

---

### Post by mc4man on 2011-07-24
> Do you need to type /dev/dvd or something like that in the end?
mplayer defaults to /dev/dev so only if the drive you're is something else
If it is you can append to command like for example if using /dev/dvd1
dvdnav:////dev/dvd1

or more permanently in ~/.mplayer/config
dvd-device=/dev/dvd1

---

### Post by beew on 2011-07-29
> **andrew.46 said:**
> Do you get dvd menu support by running the following from the commandline:

```
mplayer -mouse-movements -nocache dvdnav://
```

Hi, I tried that in Natty and Maverick (with mplayer2 and mplayer) for 2 DVDs. While the menus did show up, one played without audio and the other just crashed when I clicked the menu to choose chapter.

Both video play fine in mplayer and mplayer2 without enabling the menu.
Here is some outputs on the terminal

```
$ mplayer2 -mouse-movements -nocache dvdnav://
MPlayer2 2.0-134-g84d8671 (C) 2000-2011 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvdnav://.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: New936d_1_1_11_
....

*** libdvdread: CHECK_VALUE failed in /build/buildd/libdvdread-4.1.3/src/nav_read.c:263 ***
*** for dsi->dsi_gi.zero1 == 0 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/libdvdread-4.1.3/src/nav_read.c:263 ***
*** for dsi->dsi_gi.zero1 == 0 ***


Detected file format: MPEG-PS
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Asking decoder to use 2 threads if supported.
Selected video codec: [ffmpeg2] vfm: ffmpeg (FFmpeg MPEG-2)
==========================================================================
==========================================================================
Opening audio decoder: [dvdpcm] Uncompressed DVD/VOB LPCM audio decoder
AUDIO: 48000 Hz, 2 ch, s16be, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [dvdpcm] afm: dvdpcm (Uncompressed DVD/VOB LPCM)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
AO: [alsa] 48000Hz 2ch s16be (2 bytes per sample)
Starting playback...
[mpeg2video @ 0x87d66a0]ac-tex damaged at 38 0
[mpeg2video @ 0x87d66a0]Warning MVs not available
[mpeg2video @ 0x87d66a0]concealing 1350 DC, 1350 AC, 1350 MV errors
A:   0.3 V:   0.0 A-V:  0.000 ct:  0.000   1/  1 ??% ??% ??,?% 0 0 
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vdpau] 720x480 => 854x480 Planar YV12 
[vdpau] Got display refresh rate 59.996 Hz.
[vdpau] If that value looks wrong give the -vo vdpau:fps=X suboption manually.
A:   0.9 V:   3.8 A-V: -2.835 ct:  0.001  20/ 20 57% 197%  1.9% 0 0 
[mpeg2video @ 0x87d66a0]ac-tex damaged at 0 28
[mpeg2video @ 0x87d66a0]Warning MVs not available
[mpeg2video @ 0x87d66a0]concealing 90 DC, 90 AC, 90 MV errors


MPlayer interrupted by signal 11 in module: decode video
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.



```

Sorry for leaving the thread dangling, I have been busy with other things. :)

---

### Post by beew on 2011-07-29
While trying to play dvd with the command in #6 I also get this message in the terminal

> Too many video packets in the buffer: (4096 in 8283242 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:   0.0 V: 503.6 A-V:-503.545 ct: -0.681 216/212 12% 45% 44.8% 0 0 
Using the -ni option doesn't help and still no sound. What does that mean? The dvd plays with no problem if I don't try to enable the dvd menu.

---

### Post by beew on 2011-07-30
Hi, anyone?

---

### Post by mc4man on 2011-07-30
For one I'd either use the -vc for vdpau and mpeg, (ffmpeg12vdpau i believe),  or better yet use -vo xv instead

mplayer from cli in dvdnav can be tripped up if there is structure protection on the disk

I gather from command you're not using on a 5.1 system, there used to be an issue there, not sure if fixed
(menus are usually never 5.1, mplayer couldn't 'auto switch' when starting the main title, one needed to scroll off and back to the 5.1 stream, not an issue unless there was only 1 audio stream 

When I did use mplayer dvdnav from cli I'd just use the keyboard and keypad shortcuts, thought it performed better.
(dvdnav specific bindings are keypad ones, on a laptop  if there is  no 'keypad enter key' then that has to be changed - 'keyboard enter' will not be suitable at all

I believe I just changed the Esc to the dvdnav 'select' because I generally just used Q.
As in ~/.mplayer/input.config
```
Esc dvdnav 6
```

---

### Post by rickyrockrat on 2011-08-28
Hi, Gents. I got tired of the lack of DVD menu stuff too, so I did what any good open source citizen would do - I patched the MPlayer code so it auto-detects a DVD.  It's working for me. 

SMPlayer seems to suck badly right now.  You'll have to build mplayer, but you get DVD nav from the GUI.

Here's my writeup:
[http://ubuntuforums.org/showthread.php?p=11196383](http://ubuntuforums.org/showthread.php?p=11196383)

Cheers

---

### Post by beew on 2011-08-28
> **rickyrockrat said:**
> Hi, Gents. I got tired of the lack of DVD menu stuff too, so I did what any good open source citizen would do - I patched the MPlayer code so it auto-detects a DVD.  It's working for me. 

SMPlayer seems to suck badly right now.  You'll have to build mplayer, but you get DVD nav from the GUI.

Here's my writeup:
[http://ubuntuforums.org/showthread.php?p=11196383](http://ubuntuforums.org/showthread.php?p=11196383)

Cheers

Interesting, but I prefer to use mplayer2 and umplayer and I am no longer on Lucid so unfortunately that doesn't help me.

I am wondering why it is so difficult to support dvd menu? It is not just mplayer but it seems that dvd menu support is iffy or simply non existent in all Linux media players with the exception of VLC.

---

### Post by rickyrockrat on 2011-08-28
This works on Lucid and Natty (and anything that has libdvdread/nav 4.1.3 on it. Lucid just takes more work.

And I am with you on why this is so hard. I've asked myself that many times.

---

