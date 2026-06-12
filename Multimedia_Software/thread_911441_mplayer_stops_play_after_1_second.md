---
title: "mplayer stops play after 1 second"
date: 2008-09-05
forum: Multimedia Software
---

### Post by Daklin on 2008-09-05
Whenever I try to use mplayer to play any format of video, it will play maybe the first second and then halt play.  If you move the slider you can see the first frame or so of the new position, and in a few videos it will slow down right away and then stop.  No problems playing the videos in VLC, but since VLC can't play WMVs without scrambling them on time changes I'd prefer mplayer. 

Running a Dell Latitude with Ubuntu Hardy.

This is a new problem, and I hadn't changed any configuration files to my knowledge.  I used to have the random crash bug in Hardy where whenever opening large videos X would freeze except for the mouse, and the only option was a hard reboot.  I installed the xserver-xorg-video-intel-2.3.1 driver (instead of the 2.2.1 in the repositories) which fixed that problem, and for about 2 weeks it worked perfectly.  Now this, though - I haven't had a crash, mplayer just won't work.  Any ideas?

---

### Post by Daklin on 2008-09-06
Sorry for the bump - anyone have any ideas?

---

### Post by fujikofujio on 2008-10-19
I'm having the same exact problem on Intrepid Ibex, the problem seems to lie on mplayer, I tried using front ends such as smplayer and still got the same problem.

Anyone got any idea, been searching all over the forum and no solution yet!

---

### Post by stephanvaningen on 2008-10-19
In case you're already on Intrepid beta, Make sure you have changed your software sources of medibuntu for **Intrepid** and re-install w32codecs and libdvdcss2. My humble suggestion:
```
sudo apt-get purge w32codecs libdvdcss2
sudo apt-get clean
```
(now change the software source of medibuntu, if you don't know the info, check [medibuntu site]("https://help.ubuntu.com/community/Medibuntu"), section 'Add the repository')
Then re-install:
 ```
sudo apt-get install w32codecs libdvdcss2
```


What does this give you?

---

### Post by andrew.46 on 2008-10-21
Hi,

If you feel like living a little closer to the edge you could always try this guide to compiling the svn MPlayer under Intrepid Ibex:

[http://ubuntuforums.org/showthread.php?t=558538](http://ubuntuforums.org/showthread.php?t=558538)

This is guide that I have rewritten recently with special attention to the Intrepid Ibex section. I am running this myself (under Intrepid) and MPlayer runs beautifully.

  Andrew

---

### Post by realfstkid on 2008-10-29
I am having this same problem, but this seems to only happen when I am trying to play the DVD Casino Royale. lsdvd also goes crazy and spews out a bunch of errors.
```
*** libdvdread: CHECK_VALUE failed in ifo_read.c:1575 ***
*** for c_adt->cell_adr_table[i].start_sector < c_adt->cell_adr_table[i].last_sector ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1572 ***
*** for c_adt->cell_adr_table[i].vob_id <= c_adt->nr_of_vobs ***

```
and on and on and on like that

I am thinking this is due to encryption on the disc, but I would imagine that mplayer would have a way around it by now. 

I have libdvdcss2 and w32codecs installed, and I tried uninstalling them, but none of this worked. 

mplayer does throw a few errors, then it goes into its normal sequence, then displays the first frame of the DVD and freezes. Here is the mplayer output:

```
christian@01:37:08:~$ mplayer dvd://
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz (Family: 6, Model: 23, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
There are 99 titles on this DVD.
There are 28 chapters in this DVD title.
There are 1 angles in this DVD title.
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x05
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x06
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
*** Zero check failed in ifo_read.c:735
    for cell_position[i].zero_1 = 0x04
audio stream: 0 format: ac3 (5.1) language: en aid: 128.
audio stream: 1 format: ac3 (stereo) language: fr aid: 129.
audio stream: 2 format: ac3 (5.1) language: es aid: 130.
number of audio channels on disk: 3.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 1 language: fr
subtitle ( sid ): 2 language: es
number of subtitles on disk: 3
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 2)  29.970 fps  9800.0 kbps (1225.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x480 => 720x540 Planar YV12 
GNOME screensaver enabled.139 ct: -0.013   6/  6 ??% ??% ??,?% 0 0
```

Furthermore, the problem seems to only happen when I am trying to watch this DVD. Other DVDs (Bourne Supremacy) work just fine.

And... to complicate matters further, once I have attempted to play Casino Royale on this computer, the same thing happens with other DVD's and even video files on my computer (.mkv).

I am running Ubuntu Hardy 8.04.1 w/ Linux Kernel 2.6.24-21-generic and I have checked for any updates and have everything updated.

Thanks for anyone's help.

Christian

---

### Post by uzi09 on 2009-02-23
I've had the same problem on various versions of Ubuntu! I'm not sure, but for some reason (I think I read somewhere) it seems to be a problem with the sound device (alsa??) being used by some other program and then mplayer can't touch it. 

A restart seems to make things okay once again, however I have no idea how to test the above theory.

Any help is much appreciated.

EDIT:

The audio device seems to be something to do with Pulse Audio. Again, no idea how I could try to "restart" the device/software without having to reboot.

Also, I thought it may be a video thing instead of an audio one, but I recalled that it often happens when I try to play just audio.

I'm not using any special graphics drivers. Everything is basic on an ol' Dell Inspiron 6400/E1505.

---

### Post by emo80 on 2009-04-21
Hello all, 

I had same problem with mplayer,but I had also problem with sound in flash player.
Everything was solved after I removed pulseaudio package ;)

You can do it with these commands:
apt-get remove --purge pulseaudio-module-hal
apt-get autoremove --purge

Sorry for my English :-)

---

### Post by emo80 on 2009-05-02
> **emo80 said:**
> Hello all, 

I had same problem with mplayer,but I had also problem with sound in flash player.
Everything was solved after I removed pulseaudio package ;)

You can do it with these commands:
apt-get remove --purge pulseaudio-module-hal
apt-get autoremove --purge

Sorry for my English :-)
last update of the package pulseaudio will solve the problem. You can install it again. :-)

---

