---
title: "Problem(s) playing 1080p mkv video"
date: 2010-01-01
forum: Multimedia Software
---

### Post by opower95 on 2010-01-01
I have 9.04 and I recently "got" a 13.2GB 1080p HD movie. When I try to play it, it's choppy and mosaic like. The audio plays fine, but the video jumps and I can't get a clean picture except for maybe 15% of the time. 

I have to hold down the spacebar so it plays and pauses very quickly for the* video* to even proceed. I've updates VLC and Movie Player and I've downloaded many codecs and I can't seem to fix it.

How can I get it to play smoothly? PLEASE and thank you ahead of time.

EDIT: I can play it in Movie Player without the pixel/mosaic-like effect, but it too is extremely choppy.

---

### Post by HappyFeet on 2010-01-01
There are some things you could try on [this]("https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD") page.

---

### Post by nathanhillinbl on 2010-01-14
Bump.

Having this same problem with (ironically) the exact same sized file. My setup should be able to well handle this, and I'm getting the same results as opower95.

Asus g51vx
Nvidia Geforce GTX 260M 1GB DDR3
4GB RAM
Intel Core 2 Duo P7350 2.0 Ghz

I've also had this problem with another large 1080p file. Works fine with 720p, though.

I'm sure I speak from both opower95 and myself: Any help would be greatly appreciated!!

Thanks,
Nate


EDIT: This file is in a MKV format.

---

### Post by nathanhillinbl on 2010-01-14
I just did a mplayer -benchmark as seen in other threads, and stopped it after 2 mins with:

```
nate@nate-laptop:~/Movies/Inglourious Basterds$ mplayer -benchmark Inglourious.Basterds.2009.1080p.BluRay.DTS.x264-WiKi.mkv 
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Inglourious.Basterds.2009.1080p.BluRay.DTS.x264-WiKi.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "Video: x264_L4.1 @ 10765 Kbps", -vid 0
[mkv] Track ID 2: audio (A_DTS) "Audio: English DTS 5.1 @ 1.5 Mbps", -aid 0, -alang eng
[mkv] Track ID 3: subtitles (S_TEXT/UTF8) "English_SDH", -sid 0, -slang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x800  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [libdca] DTS decoding with libdca
Stream with high frequencies VQ coding
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [dts] afm: libdca (DTS-libdca)
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1920 x 800 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.40:1 - prescaling to correct movie aspect.
VO: [xv] 1920x800 => 1920x800 Planar YV12 
[ASPECT] Warning: No suitable new res found!
A: 105.7 V: 105.7 A-V: -0.001 ct: -0.001   0/  0 24% 16%  5.5% 99 0 

MPlayer interrupted by signal 2 in module: key_events
A: 105.7 V: 105.7 A-V: -0.001 ct: -0.001   0/  0 24% 16%  5.4% 99 0 
Exiting... (Quit)
nate@nate-laptop:~/Movies/Inglourious Basterds$ 

```

---

### Post by nathanhillinbl on 2010-01-14
After some more searching, I figured that my CPU was the limitation, and that VLC/Mplayer wasn't offloading any of the .mkv decoding to the video card, and that this could be done with gnome-mplayer, or any media player that can output video to vdpau. 

Note: In gnome-mplayer (different than regular mplayer), you have to set the video output in the Preferences dialog to vdpau for this to work. Mplayer and VLC both do not support outputting to vdpau. I just changed the default program for viewing .mkv's to gnome-mplayer.

---

### Post by shirilover on 2010-01-14
> **nathanhillinbl said:**
> After some more searching, I figured that my CPU was the limitation, and that VLC/Mplayer wasn't offloading any of the .mkv decoding to the video card, and that this could be done with gnome-mplayer, or any media player that can output video to vdpau. 

Note: In gnome-mplayer (different than regular mplayer), you have to set the video output in the Preferences dialog to vdpau for this to work. Mplayer and VLC both do not support outputting to vdpau. I just changed the default program for viewing .mkv's to gnome-mplayer.

To use vdpau, you need to have a supported nvidia video card and be using a recent driver. Also, mplayer has to be built with vdpau support. to use vdpau with mplayer you can just do:
mplayer -vo vdpau -vc ffh264vdpau yourvideo.mkv

gnome-mplayer is just a gtk+ front-end to mplayer, there is no difference between the two.

---

