---
title: "MOV Files in Ubuntu Feisty 7.04"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by antex on 2007-05-25
Despite having installed just about every codec package I can come across, I can not play .mov files on my computer. VLC displays the first frame of video and plays the audio, Totem gives "GStreamer encountered a general stream error" upon opening it and gxine is the only thing which displays video and audio but it experiences a degradation in quality. Totem-xine doesn't work, and MPlayer gives the error, "Error opening/initializing the selected video_out (-vo) device."

Help? *Anyone.*

---

### Post by inkybutton on 2007-05-25
1) can you open a terminal, enter:

$ mplayer [file's name]

and post the output here?

Thanks.

---

### Post by antex on 2007-05-26
Sorry for the lateness in the response, I got sidetracked by a few other things.

Interesting, when I run mplayer from terminal, it actually loads as soon as the last line of the following comes up.

```
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Celeron(R) CPU 2.93GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing rails_take2_with_sound.mov.
ISO: File Type Major Brand: Original QuickTime
Quicktime/MOV file format detected.
VIDEO:  [rle ]  970x754  32bpp  5.000 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffqtrle] vfm: ffmpeg (QuickTime Animation (RLE))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 1 ch, s16le, 64.0 kbit/9.07% (ratio: 8000->88200)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 970 x 754 (preferred colorspace: BGRA)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using BGRA as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8

SwScaler: BICUBIC scaler, from rgb32 to yuv420p using MMX2
SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
SwScaler: using 1-tap MMX "scaler" for vertical scaling (YV12 like)
SwScaler: 970x754 -> 970x754
VO: [xv] 970x754 => 970x754 Planar YV12 
A:  12.5 V:  12.5 A-V: -0.026 ct:  0.489  65/ 65  1% 18%  0.7% 22 0 
Exiting... (Quit)

```

After this it returns to a regular terminal line waiting for input, but there's a single MPlayer window open with nothing but video; there's no menu or buttons, etc. Also, from what I can remember, the quality isn't as good as it used to be when I could last play .mov as normal.

Perhaps it's something to do with
```
Quicktime/MOV file format detected.
VIDEO:  [rle ]  970x754  32bpp  5.000 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffqtrle] vfm: ffmpeg (QuickTime Animation (RLE))
```

?

**EDIT:** Sorry, it doesn't actually return to a waiting-for-input terminal line, it's just that when I ran it, I had the terminal window behind the MPlayer window. </stupid_mistake>

---

### Post by antex on 2007-05-26
By the way, I should probably point out that xserver-xorg-video-mga is actually installed.

---

### Post by antex on 2007-05-26
I have a solution.

For some reason, there are "late frames" when playing it under the default driver -- which I haven't ascertained yet -- but setting the default driver to x11, or running it in terminal with -vo x11 loads it up fine. In VLC, if I disable "drop late frames" under advanced options, it will play the video but there will be overlaps in the playback.

This doesn't entirely explain why totem-gstreamer fails, along with mplayer when using the default driver.

---

