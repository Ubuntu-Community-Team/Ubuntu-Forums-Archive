---
title: "no alsa or esd voice output... :("
date: 2005-11-28
forum: Multimedia &amp; Video
---

### Post by vvlaw on 2005-11-28
There are no alsa or esd menu at the mplayer's voice configuration.
so  i can't select these two drivers to play movie...

i tried to open the avi files with commandline .but it can be work :( 

~~~~~~~~~~~~~~~~~~~~
$ mplayer -ao alsa  *.avi -sub *.chs.srt
MPlayer 1.0pre7try2-3.4.5 (C) 2000-2005 MPlayer Team
CPU: Advanced Micro Devices  (Family: 8, Stepping: 2)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2


85 audio & 196 video codecs
Cannot load font: /usr/share/fonts/zh_CN/TrueType/SIMSUN.TTF
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Playing se7en-speed.cd1.avi.
AVI file format detected.
VIDEO:  [XVID]  800x332  12bpp  23.976 fps  1537.8 kbps (187.7 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2540/release)
SUB: Detected subtitle file format: subviewer
SUB: Read 387 subtitles.
SUB: added subtitle file (1): se7en-speed.cd1.chs.srt
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'dts' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found
hwac3: switched to DTS, 768000 bps, 48000 Hz
AUDIO: 48000 Hz, 2 ch, ac3, 768.0 kbit/50.00% (ratio: 96000->192000)
Selected audio codec: [hwdts] afm:hwac3 (DTS through S/PDIF)
==========================================================================
vo: X11 running at 1024x768 with depth 24 and 32 bpp (":0.0" => local display)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm:ffmpeg (FFmpeg MPEG-4)
==========================================================================
Checking audio filter chain for 48000Hz/2ch/ac3 -> 48000Hz/2ch/ac3...
AF_pre: 48000Hz/2ch/ac3
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
VDec: vo config request - 800 x 332 (preferred csp: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.41:1 - prescaling to correct movie aspect.
VO: [xv] 800x332 => 800x332 Planar YV12
V:   1.6  40/ 40  7%  1%  0.0% 0 0
Exiting... (Quit)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

any advise?

---

### Post by amohanty on 2005-11-28
Have you setup the device in
System->Preferences->Multimedia Systems Selector

And if you choose esd, make sure to goto:
System->Preferences->Sound 
and make sure that you check the 
Enable Sound Server
option

HTH
AM

---

### Post by vvlaw on 2005-11-28
[QUOTE=amohanty]Have you setup the device in
System->Preferences->Multimedia Systems Selector

And if you choose esd, make sure to goto:
System->Preferences->Sound 
and make sure that you check the 
Enable Sound Server
option

HTH
AM[/QUOTE]

System->Preferences->Multimedia Systems Selector,if i select the i"output" set the  "alsa"or"esd",it can be pass test.but if i set the output is "esd".it can be passed, but no any voice.if i set the output is "alsa",it show the errors... :( 

i'm sure that in this way "System->Preferences->Sound "

i enabled the sound server already... but the mplayer's voice perferences has no alsa or esd selection. :confused:

---

### Post by amohanty on 2005-11-28
OK try installing the following:

totem-xine (this will uninstall totem-gstreamer)
w32codecs
libdvdcss2

Unfortunately I dont have access to my box right now, but look around the forums, there are tons of posts as to how to install w32codecs and libdvdcss2

HTH
AM

---

