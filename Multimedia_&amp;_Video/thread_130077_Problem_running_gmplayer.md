---
title: "Problem running gmplayer"
date: 2006-02-15
forum: Multimedia &amp; Video
---

### Post by swong1 on 2006-02-15
Hi, when I try to run gmplayer, I get the following error message:
```

MPlayer dev-CVS--4.0.2 (C) 2000-2005 MPlayer Team
CPU: Intel  (Family: 6, Stepping: 8)
Detected cache-line size is 64 bytes
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for Debian.



vo: X11 running at 1280x800 with depth 24 and 32 bpp (":0.0" => local display)
86 audio & 200 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
**Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.**
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

```
I have mplayer, but gmplayer can't find it. How do I fix it? Thanks for your help.

---

### Post by swong1 on 2006-02-19
Bum. Can somebody please help me with this problem? Also, where can I find the startup script?

---

### Post by jazzi on 2006-03-05
try to change the 
vo=x11 to vo=xv
may it works

---

