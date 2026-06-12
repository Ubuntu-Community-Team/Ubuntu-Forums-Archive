---
title: "Mplayer &amp; ATI X1400 in edgy"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by punkinside on 2006-10-28
I don't understand this, I've googled and searched the forums but nobody else seems to have this problem. I've followed the wiki howto for installing the ati driver in edgy. 

Everything seems to go peachy:

```

punk@Adrian:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

```

punk@Adrian:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
1441 frames in 5.0 seconds = 288.200 FPS
1512 frames in 5.0 seconds = 302.400 FPS
1566 frames in 5.0 seconds = 313.200 FPS
1511 frames in 5.0 seconds = 302.200 FPS

```

```

punk@Adrian:~$ glxinfo | grep rendering
direct rendering: Yes

```

BUT! When I try to see movies with mplayer, I get an error with something about an video output device. So I try again from the command line to see whats happening and I get this:

```

punk@Adrian:/media/LACIE/Movies & Videos/Simpson/Simpsons Season 18$ mplayer the.simpsons.1801.pdtv-lol.\[VTV\].avi -vo xv
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2500  @ 2.00GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
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

Playing the.simpsons.1801.pdtv-lol.[VTV].avi.
AVI file format detected.
VIDEO:  [XVID]  512x384  12bpp  23.976 fps  1015.3 kbps (123.9 kbyte/s)
Clip info:
 Software: VirtualDub
==========================================================================
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 134.1 kbit/8.73% (ratio: 16757->192000)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
==========================================================================
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
Error opening/initializing the selected video_out (-vo) device.

```

The output of xvinfo is:
```
punk@Adrian:/media/LACIE/Movies & Videos/Simpson/Simpsons Season 18$ xvinfo
X-Video Extension version 2.2
screen #0
 no adaptors present
```

this is even after doing a few times

```
 sudo aticonfig --overlay-type=Xv 
```

Videos play fine using -vo gl even though my xorg clearly states 

Option     "OpenGLOverlay" "off"

any ideas?!

---

### Post by alanpotpot on 2006-10-29
I am using an X1600 and has the same error(no XVideo).

---

### Post by purth on 2006-10-29
I am using a x1400 and have the same problem.
It seems to be a known issue with the new fglrx driver.

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.29.6.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.29.6.html)

Just have a look under known issues.
Let's hope ati fixes this problem soon.

---

