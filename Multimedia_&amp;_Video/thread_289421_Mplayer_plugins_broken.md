---
title: "Mplayer plugins broken"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by SmiLey497 on 2006-10-30
The plugins 

mplayerplug-in-gmp.so 
mplayerplug-in-gmp.xpt


in my firefox plugin folder are broken how do i fix them](*,)

---

### Post by tommcd on 2006-10-31
How did you discover they are broken? I am having a problem with mplayer and the plugin playing mpeg videos. I did notice that in /usr/lib/firefox/plugins those 2 plugins have a little "x" beide them. I wasn't sure if that meant they were broken, oe just not being used for some reason. btw, can your mplayer play mpeg videos at all? Does your mplayer plugin work?

---

### Post by tommcd on 2006-10-31
Did you find a solution to this? I still have not been able to fix it. Reinstalling has not helped.

---

### Post by space42 on 2006-10-31
I am having the same issue. I am missing those two plugins.  There are symbolic links but they are broken.
My mplayer plug-in is not working.  It buffers and restarts constantly.
This worked fine on 6.6 and broke after the 6.10 upgrade.

any ideas?

---

### Post by russianpirate on 2006-10-31
You dont need them.
Just [download  this](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb) and install it with apt-get. THEN, you can use mplayer to play wmvs and mpegs. Also make sure libmpeg (or just search mpeg) is installed.

---

### Post by tommcd on 2006-10-31
Thanks for the reply RussianPirate. I do have the w32 codecs installed. I am not sure about libmpeg. I am at work now, so I will how have to check on that when I get home. When you said "You dont need them", did you mean we can delete them? Do you have those 2 plugins in /usr/lib/firefox/plugins? and are they listed as broken?
I can stream wmv videos just fine with totem. I can download mpegs and watch them with totem or vlc, just not mplayer. Mplayer will play wmv and avi videos that I download, just not mpegs. I think it is all related to those 2 broken plugins. I can't find anything else wrong.
I'm getting closer to solving this. Any further advice appreciated, thanks.

---

### Post by SmiLey497 on 2006-11-01
> **tommcd said:**
> How did you discover they are broken? I am having a problem with mplayer and the plugin playing mpeg videos. I did notice that in /usr/lib/firefox/plugins those 2 plugins have a little "x" beide them. I wasn't sure if that meant they were broken, oe just not being used for some reason. btw, can your mplayer play mpeg videos at all? Does your mplayer plugin work?



i checked the properties, mplayer works in some sights but in som esights it starts then buffers than hangs a 99 percent

---

### Post by SmiLey497 on 2006-11-01
> **russianpirate said:**
> You dont need them.
Just [download  this](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb) and install it with apt-get. THEN, you can use mplayer to play wmvs and mpegs. Also make sure libmpeg (or just search mpeg) is installed.

i downloaded these through automatx

---

### Post by SmiLey497 on 2006-11-01
i noticed mplayer works fine with quicktime viedoes form apple.com and such but if its a wma, wmv file it stops completely or at 99 percent buffering

---

### Post by tommcd on 2006-11-01
Well I noticed you can 'fix' the 2 broken plugins by creating dummy files named mplayerplug-in-gmp.so and mplayerplug-in-gmp.xpt in /usr/lib/mozilla/plugins for the broken plugins to link to. Unfortunately this does not fix my problem. I searched synaptic and installed all the libmpeg plugins and I still can't stream mpeg videos.
If I launch mplayer from terminal and try to play a mpeg video I get this error:

MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 47, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
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
** (<unknown>:21613): CRITICAL **: mist_draw_border: assertion `shadow_type != GTK_SHADOW_NONE' failed
*****
==========================================================================
==========================================================================
Trying to force video codec driver family dshow...
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 448 x 256 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
alsa-init: using device default
alsa-init: format mpeg2 are not supported by hardware, trying default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
[format] Sample format big-endian MPEG-2 not yet supported 
Couldn't find matching filter/ao format!
Starting playback...

Anybody else get this? I've tried googling some of this stuff without finding any help.

---

### Post by tommcd on 2006-11-06
Well I fixed this problem. In case anyone else runs into this, just open mplayer>preferences>codecs & demuxer, and select FFmpeg's libavcodec codec family for video codecs family and FFmpeg/libavcodec audio decoders for audio codecs. Then restart mplayer. 
Still working on streaming mpegs from web pages. I can stream wmv files, just not mpegs.
Smiley, did you get yours going yet??

---

