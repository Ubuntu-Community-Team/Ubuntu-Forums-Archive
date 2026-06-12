---
title: "Video problems on Inspiron 6000"
date: 2006-01-20
forum: Multimedia &amp; Video
---

### Post by Aybara on 2006-01-20
I'm a newbie and I have just installed Breezy on my Inspiron 6000. Most things worked after install, but I have some problems with video (and audio) playback.

When I try to open videos in totem or mplayer things don't go very well. I have chosen XWindows (noXv) and Video for Linux (v4l) for sink and source in the Multimedia Systems Selector. When I run mplayer from the Application menu everything just hangs, and when I run them from the command line the following is output:

anders@ubuntu:~/tmp$ sudo mplayer Royksopp\ -\ What\ Else\ Is\ There.mpg
Password:
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Intel  (Family: 6, Stepping: 8)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for Debian.


86 audio & 200 video codecs
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing Royksopp - What Else Is There.mpg.
MPEG-PS file format detected.
VIDEO:  MPEG2  480x576  (aspect 2)  25.000 fps  2496.0 kbps (312.0 kbyte/s)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 384.0 kbit/27.21% (ratio: 48000->176400)
Selected audio codec: [mad] afm:libmad (libMAD MPEG layer 1-2-3)
==========================================================================
vo: X11 running at 1680x1050 with depth 24 and 32 bpp (":0.0" => local display)
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
open: No such file or directory
vo_mga: Couldn't open /dev/mga_vid
open: No such file or directory
vo_mga: Couldn't open /dev/mga_vid
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 480 x 576 (preferred csp: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm:libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/60208 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bps)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 480 x 576 (preferred csp: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [3dfx] 480x576 => 768x576 Planar YV12
Couldn't open /dev/3dfx

My pc has a ATI Radeon Mobile X300 card, and I have done nothing at all to configure it... I installed another display driver than the default one after some googling told me I should do it... I installed win32-codecs or something like that.

Anyone got any ideas as to what is wrong?? Totem seemed to work with mpg files, but not with avi.

---

