---
title: "mplayer not openning any file"
date: 2007-02-21
forum: Multimedia &amp; Video
---

### Post by kanha on 2007-02-21
i am frustrated now.any time i try to open a file in mplayer it says fatal error
[COLOR="Red"]error openning/initializing the selected video output (-vo) device[/COLOR]
then i tried openning it through terminal here is output:confused: 
[COLOR="Red"]kanha@vachaspati:~$ gmplayer
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 2800+ (Family: 15, Model: 4, Stepping: 10)
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
GTK Accessibility Module initialized
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed

Playing /media/Video/bollywood songs/Aish/KajraRe.avi.
AVI file format detected.
VIDEO:  [DX50]  640x288  12bpp  23.976 fps  799.8 kbps (97.6 kbyte/s)
==========================================================================
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 128.7 kbit/8.38% (ratio: 16089->192000)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
==========================================================================
open: No such file or directory
Couldn't open: /dev/mga_vid
Error opening/initializing the selected video_out (-vo) device.


Exiting... (Quit)
[COLOR="Black"]then again tried installing it[/COLOR]
kanha@vachaspati:~$ sudo apt-get install mplayer
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mplayer is already the newest version.
The following packages were automatically installed and are no longer required:
  dctc
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kanha@vachaspati:~$ gmplayer
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 2800+ (Family: 15, Model: 4, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.[/COLOR]



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
GTK Accessibility Module initialized

---

### Post by RomeReactor on 2007-02-21
Hi. Open Mplayer, go to "Preferences-->Video" and select the **xv    X11/Xv** driver; close Mplayer, open it again and try to play the file now.

---

### Post by kanha on 2007-02-21
> **RomeReactor said:**
> Hi. Open Mplayer, go to "Preferences-->Video" and select the **xv    X11/Xv** driver; close Mplayer, open it again and try to play the file now.

worked,now it is playing everything
thank you for help
though starting mplayer shows a error mp3 format not found enable it at compilation
or something like that
what is that?
i can't understand

---

### Post by taurus on 2007-02-21
Applications -> Sound & Video -> Mplayer -> Preferences -> Codecs & demux:

Video codec family:  FFmpeg's libavcodec codec family
Audio codec family:  FFmpeg/libavcodec audio decoders

---

### Post by kanha on 2007-02-22
thanx
everything working now.

---

