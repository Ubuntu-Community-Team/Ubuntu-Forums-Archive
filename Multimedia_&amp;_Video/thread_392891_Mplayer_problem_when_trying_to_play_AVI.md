---
title: "Mplayer problem when trying to play AVI"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by zupidupi on 2007-03-25
Hiya folks,

I'm trying to play an AVI-file with mplayer on my Ubuntu-box running in console mode. I have a DVB-card connected to the telly which I'd like to use for the output.

The following command

mplayer -vo mpegpes:card=2 -ao mpegpes:card=2 -vc mpegpes movie.avi

gives the following output:

<----- START

MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm) Processor 2800+ (Family: 15, Model: 44, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not open config files /home/misha/.lircrc and /etc/lircrc
mplayer: No such file or directory
Failed to read LIRC config file ~/.lircrc.
You will not be able to use your remote control.

Playing bl60.avi.
AVI file format detected.
VIDEO:  [XVID]  640x352  12bpp  29.970 fps  785.0 kbps (95.8 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.1 (build 2439/release)
==========================================================================
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 122.3 kbit/7.96% (ratio: 15292->192000)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
==========================================================================
Opening /dev/dvb/adapter1/video0+audio0
==========================================================================
Forced video codec: mpegpes
Cannot find codec matching selected -vo and video format 0x44495658.
Read DOCS/HTML/en/codecs.html!
==========================================================================
Could not open/initialize audio device -> no sound.
Audio: no sound
Video: no video


Exiting... (End of file)

-----> STOP

I read the codecs.html-site, but it didn't make me much wiser. I have downloaded and installed the essential codecs, but still no success.

Tell me, experts, what am I missing here, what should I do to make the system work? I might add that MPEG:s show up fine, it's just the AVI:s that are uncooperative.

Thx in advance,

   Mike

---

### Post by krugger on 2007-03-25
Xvid is MPEG-4, you need to first mencoded it to mpeg2

---

