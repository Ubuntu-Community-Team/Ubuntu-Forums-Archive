---
title: "gmplayer won't play an mms stream but mplayer will?"
date: 2008-04-23
forum: Multimedia Software
---

### Post by itchanddino on 2008-04-23
Whenever I try to load an mms stream with gmplayer, it crashes on me.  But if I launch the CLI version of mplayer, it plays the stream fine.  Here are the messages:

gmplayer 
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3400+ (Family: 15, Model: 4, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mms://137.140.50.4:8080.
STREAM_ASF, URL: mms://137.140.50.4:8080
Resolving 137.140.50.4 for AF_INET6...
Couldn't resolve name for AF_INET6: 137.140.50.4
Connecting to server 137.140.50.4[137.140.50.4]: 8080...
Connected

Alert! EOF


MPlayer interrupted by signal 13 in module: open_stream
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.


_Now with Mplayer_

 mplayer mms://137.140.50.4:8080
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3400+ (Family: 15, Model: 4, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mms://137.140.50.4:8080.
STREAM_ASF, URL: mms://137.140.50.4:8080
Resolving 137.140.50.4 for AF_INET6...
Couldn't resolve name for AF_INET6: 137.140.50.4
Connecting to server 137.140.50.4[137.140.50.4]: 8080...
Connected

Alert! EOF
read error:: Operation now in progress
pre-header read failed
Resolving 137.140.50.4 for AF_INET6...
Couldn't resolve name for AF_INET6: 137.140.50.4
Connecting to server 137.140.50.4[137.140.50.4]: 8080...
Resolving 137.140.50.4 for AF_INET6...
Couldn't resolve name for AF_INET6: 137.140.50.4
Connecting to server 137.140.50.4[137.140.50.4]: 8080...
Cache size set to 64 KBytes
Cache fill: 12.50% (8192 bytes)   
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 name: WFNP 88.7 FM
 author: The Edge
 comments: The Cutting Edge of the Hudson Valley
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4003->88200)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [pulse] 22050Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:726963.2 (201:56:03.2) of 2133437440.0 (-24.-8)  0.5% 0% 


Any ideas?  Also, mms streams do not work in totem for me, but they DO work in VLC.  Thank you!

---

### Post by cor2y on 2008-04-25
try totem-xine and not totem-gstreamer it has some problems with non standard asf streams, as for the mplayer problem you may need to configure gmplayer a bit before you can get playback.
I had an avi file would crash gmplayer but play flawlessly in mplayer the reason was the audio codec i was using in gmplayer (toolame i think) as output, setting it to libmad which mplayer uses as default if it is installed fixed the issue for me could be something similar with your problem.

---

