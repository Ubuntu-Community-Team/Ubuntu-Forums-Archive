---
title: "mplayer video and sound jerky"
date: 2005-11-01
forum: Multimedia &amp; Video
---

### Post by holymadness83 on 2005-11-01
hiyas,
just trying out ubuntu.

i got nvidia drivers up and installed mplayer using the apt-get and edited the mplayer.conf file from vo=x11 to vo=xv.

otherwise, i only used apt-get.

i get this when i go to play a movie file:
MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Intel Pentium 4/Xeon/Celeron Northwood (Family: 8, Stepping: 4)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for Debian.


86 audio & 200 video codecs
Failed to open /dev/rtc: Device or resource busy (it should be readable by the user.)
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing jaja11.asf.
ASF file format detected.
VIDEO:  [WMV2]  320x240  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Trying to force audio codec driver family libmad...
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 64.0 kbit/4.54% (ratio: 8005->176400)
Selected audio codec: [ffwmav2] afm:ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
vo: X11 running at 1280x1024 with depth 24 and 32 bpp (":0.0" => local display)
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Decoder supports the following YUV formats: YUY2 IYUV UYVY YV12 YVYU I420 YVU9
Decoder is capable of YUV output (flags 0x7f)
VDec: vo config request - 320 x 240 (preferred csp: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 320x240 => 320x240 Planar YV12
Selected video codec: [wmv8] vfm:dshow (Windows Media Video 8)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/60208 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bps)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Starting playback...
alsa-space: xrun of at least 0.052 msecs. resetting stream?,?% 0 0 80%
alsa-space: xrun of at least 0.053 msecs. resetting stream?,?% 1 0 77%
alsa-space: xrun of at least 0.052 msecs. resetting stream1.5% 2 0 71%
alsa-space: xrun of at least 0.054 msecs. resetting stream1.2% 4 0 66%
alsa-space: xrun of at least 0.055 msecs. resetting stream1.1% 5 0 65%
alsa-space: xrun of at least 0.055 msecs. resetting stream1.0% 6 0 60%
alsa-space: xrun of at least 0.053 msecs. resetting stream0.9% 7 0 58%
alsa-space: xrun of at least 0.052 msecs. resetting stream0.8% 8 0 54%
alsa-space: xrun of at least 0.054 msecs. resetting stream0.8% 9 0 49%
alsa-space: xrun of at least 0.053 msecs. resetting stream0.8% 10 0 46%
alsa-space: xrun of at least 0.055 msecs. resetting stream1.0% 11 0 46%
alsa-space: xrun of at least 0.056 msecs. resetting stream0.9% 12 0 46%
alsa-space: xrun of at least 0.055 msecs. resetting stream0.9% 13 0 46%
alsa-space: xrun of at least 0.056 msecs. resetting stream0.9% 14 0 45%


now the interesting part is the "alsa-space: xrun of at least...."

i can't figure out what's causing that.  divx plays, wmv's play, everything plays, but it jerks and skips and skunks all over my screen :(

can anyone help me?

thanks!  btw, ubuntu is the best distro yet.

---

### Post by holymadness83 on 2005-11-01
another point of interest!

when i run mplayer -nosound, the video is FINE, 100%.

so it's a sound problem, as i gathered from the word alsa being involved.

thanks again

---

### Post by holymadness83 on 2005-11-01
ok, i tried to compile mplayer myself and avoided the sound problem, but other problems cropped up.  i still want to use the apt-get release, so i'm going to remove the other one, but it proved to me that mplayer CAN work with my hardware, etc.  would it help if i posted my mplayer.conf file?

---

### Post by holymadness83 on 2005-11-01
alright, i fixed it.  (no thanks to any of you might i add :p grrr :p)

i added this line to my mplayer.conf file (would also work in .mplayer/config in home directory.  i sim linked 'em together)

srate=48000


and that did the trick.  works fine now, my programs just fight over the sound card a bit.  but running by themselves, all is well.

---

