---
title: "Mplayer xvid problem"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by mamboze on 2008-04-14
Hi,

I have problem with Mplayer being unable to play an  xxx.HDTV_Xvid.FoV.avi file on Gutsy.  I've got the avifile-xvid-plugin installed and vlc-plugin-esd (got this from another forum thread). But running mplayer still gives error message "Failure to open file: ......."   

I've checked out forums, rebooted but no success.

I also tried Totem but it gave this message:   

Video codec 'XviD' is not handled. You might need to install additional plugins to be able to play some types of movies


I've run out of ideas and would be grateful of any help.

---

### Post by simonn on 2008-04-14
Can try playing the file using mplayer from the command line and post the complete output?

---

### Post by mamboze on 2008-04-15
Hi,
Mplayer worked from the command line   video and audio excellent 

roy@prospero:~$ mplayer /home/roy/azureus/Underbelly.1x01_1x02.The_Black_Prince.Sorcerers_Apprentice.HDTV_XviD-FoV.avi
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/roy/azureus/Underbelly.1x01_1x02.The_Black_Prince.Sorcerers_Apprentice.HDTV_XviD-FoV.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  640x368  16bpp  25.000 fps  1023.7 kbps (125.0 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[VO_XV] Could not grab port 325.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 368 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.74:1 - prescaling to correct movie aspect.
VO: [xv] 640x368 => 640x368 Planar YV12 
A:3762.0 V:3762.0 A-V: -0.002 ct:  0.011 94052/94052  5%  0%  2.0% 15 0 

MPlayer interrupted by signal 2 in module: sleep_timer
gnome_screensaver_control()roy@prospero:~$ mplayer /home/roy/azureus/Underbelly.Sorcerers_Apprentice.HDTV_XviD-FoV.avi
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/roy/azureus/Underbelly.1x01_1x02.The_Black_Prince.Sorcerers_Apprentice.HDTV_XviD-FoV.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  640x368  16bpp  25.000 fps  1023.7 kbps (125.0 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
[VO_XV] Could not grab port 325.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 368 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.74:1 - prescaling to correct movie aspect.
VO: [xv] 640x368 => 640x368 Planar YV12 
gnome_screensaver_control()01 ct:  0.009 558/558  7%  0%  1.9% 1 0 
Exiting... (Quit)

One question tho why doesn't Mplayer GUI work? 

thanks

---

### Post by mamboze on 2008-04-15
Duh, included 2 runs of video. 

I wonder if you could tell me what the following output means?

mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

thanks

---

### Post by simonn on 2008-04-15
Try:

mplayer /home/roy/azureus -vo x11 /Underbelly.1x01_1x02.The_Black_Prince.Sorcerers_Apprentice.HDTV_XviD-FoV.avi

---

### Post by mamboze on 2008-04-15
the -vo x11 options prevent the screen maximizing, a black border is left around the images, I've tried 3 files - same effect. 

command line output seems to be the same

roy@prospero:~$ mplayer -vo x11 /home/roy/azureus/Underbelly.1x01_1x02.The_Black_Prince.Sorcerers_Apprentice.HDTV_XviD-FoV.avi
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/roy/azureus/Underbelly.1x01_1x02.The_Black_Prince.Sorcerers_Apprentice.HDTV_XviD-FoV.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  640x368  16bpp  25.000 fps  1023.7 kbps (125.0 kbyte/s)
Clip info:
 Software: Nandub v1.0rc2
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 368 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.74:1 - prescaling to correct movie aspect.
VO: [x11] 640x368 => 640x368 Planar YV12 
[swscaler @ 0x8925250]SwScaler: using unscaled yuv420p -> rgb32 special converter
gnome_screensaver_control()13 ct:  0.008 373/373  8%  4%  2.2% 1 0 
Exiting... (Quit)

---

### Post by sloggerkhan on 2008-04-15
I don't know what mplayer GUI you are using, but I've found the only one which works to my satisfaction is smplayer, found here: [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)
deb here: [http://downloads.sourceforge.net/smplayer/smplayer_0.6.0rc4_i386.deb](http://downloads.sourceforge.net/smplayer/smplayer_0.6.0rc4_i386.deb)

---

### Post by mamboze on 2008-04-15
Hi Sloggerkhan,
The reason mplayer wasn't working was that I had it pointing to the wrong folder !!! Once I sorted that out, the GUI worked OK, but I installed SMPlayer anyhow and it looks very good, plenty of features.

thanks

---

