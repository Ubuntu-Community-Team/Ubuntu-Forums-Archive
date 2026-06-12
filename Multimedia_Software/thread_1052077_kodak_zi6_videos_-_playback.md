---
title: "kodak zi6 videos - playback"
date: 2009-01-27
forum: Multimedia Software
---

### Post by vajorie on 2009-01-27
does anyone here have a kodak zi6? I tried playing back movies from it and vlc cuts the sound at the middle and starts skipping toward the end. mplayer keeps skipping and the sound is choppy for both players. mplayer gives the following errors (see end): 
```

$ mplayer Desktop/Zi6_0478.MOV 
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Desktop/Zi6_0478.MOV.
ISO: File Type Major Brand: Original QuickTime
Quicktime/MOV file format detected.
[mov] Video stream found, -vid 0
[mov] Audio stream found, -aid 1
VIDEO:  [avc1]  1280x720  24bpp  59.960 fps    0.0 kbps ( 0.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[h264 @ 0x89398d0]AVC: Consumed only 25 bytes instead of 28
[h264 @ 0x89398d0]AVC: nal size 0
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
[h264 @ 0x89398d0]AVC: Consumed only 7765 bytes instead of 77682 0 
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 27765 bytes instead of 277680 
[h264 @ 0x89398d0]AVC: nal size 0
[h264 @ 0x89398d0]AVC: Consumed only 27397 bytes instead of 274000 
[h264 @ 0x89398d0]AVC: nal size 0

```

ffplay can't play it either (choppy sound and video skips). It gives the following errors: 
```

$ ffplay Desktop/Zi6_0478.MOV 
[mov,mp4,m4a,3gp,3g2,mj2 @ 0xb7f3e110]negative ctts, ignoring
[h264 @ 0xb7e4c9a8]AVC: Consumed only 25 bytes instead of 28
[h264 @ 0xb7e4c9a8]AVC: nal size 0
[h264 @ 0xb7e4c9a8]AVC: Consumed only 7765 bytes instead of 7768
[h264 @ 0xb7e4c9a8]AVC: nal size 0
[h264 @ 0xb7e4c9a8]AVC: Consumed only 27765 bytes instead of 27768
[h264 @ 0xb7e4c9a8]AVC: nal size 0
[h264 @ 0xb7e4c9a8]AVC: Consumed only 27397 bytes instead of 27400
[h264 @ 0xb7e4c9a8]AVC: nal size 0
[h264 @ 0xb7e4c9a8]AVC: Consumed only 99229 bytes instead of 99232
[h264 @ 0xb7e4c9a8]AVC: nal size 0

```

any pointers appreciated :) thanks

PS. tried both 'vga', 'hd', and 'hd60' options. same thing, except that the problem manifests itself as bad sync btw audio and video in 'vga' mode.

---

### Post by egmichau on 2009-02-28
I refer here to the Zi6 HD30 video setting and Zi6 reported firmware version 1.10. (I did not use other formats extensively.)

I have found that FFMPEG can convert this mpeg4 format to a more usual mpeg4 file format well handled by the video players and editing tools found in the linux world.

That said, FFMPEG has to be recompiled because the version compiled for Ubuntu (8.04 in my case) does not use libfaad library. Note that Zi6 files are reported by my tools to contain AAC encoded audio.

With this specially recompiled FFMPEG, I use the simple command:

ffmpeg -i Zi6_file.MOV -sameq Zi6_correctfile.MOV

Then, the resulting file can notably be converted to DV by Kino. (Kino version 1.1.1). Note that this version of Kino looses HD additional resolution in the DV conversion process. This is reportedly better in recent versions.

> **vajorie said:**
> does anyone here have a kodak zi6? I tried playing back movies from it and vlc cuts the sound at the middle and starts skipping toward the end. mplayer keeps skipping and the sound is choppy for both players. mplayer gives the following errors ...

---

### Post by vajorie on 2009-03-01
> **egmichau said:**
> I refer here to the Zi6 HD30 video setting and Zi6 reported firmware version 1.10. (I did not use other formats extensively.)

I have found that FFMPEG can convert this mpeg4 format to a more usual mpeg4 file format well handled by the video players and editing tools found in the linux world.

That said, FFMPEG has to be recompiled because the version compiled for Ubuntu (8.04 in my case) does not use libfaad library. Note that Zi6 files are reported by my tools to contain AAC encoded audio.

With this specially recompiled FFMPEG, I use the simple command:

ffmpeg -i Zi6_file.MOV -sameq Zi6_correctfile.MOV

Then, the resulting file can notably be converted to DV by Kino. (Kino version 1.1.1). Note that this version of Kino looses HD additional resolution in the DV conversion process. This is reportedly better in recent versions.

thanks, I'll try this as soon as possible. 

by the way, what do you do with the resulting dv file? just burn to a dvd? can regular dvd players recognize that? any pointers about this stuff appreciated :)

---

### Post by gizmobay on 2009-05-13
I recently purchased the Zi6 and I tried viewing the file with vlc/mplayer and I received the same issues. I compiled ffmpeg and did the convert above. The file size almost doubled in size and the quality was poor. Anyone know how I can alter the command to keep better quality even if I have to change the format?

---

