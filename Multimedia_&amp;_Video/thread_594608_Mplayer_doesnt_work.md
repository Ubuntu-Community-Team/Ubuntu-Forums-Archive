---
title: "Mplayer doesnt work"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by Pulshion on 2007-10-28
It used to work but now it doesnt

here is the output:

```

dmitriy@linux:~/Desktop$ gmplayer cristiano_ronaldo_vs_dinamo__kiev_by_cronaldo7.wmv 
MPlayer 2:1.0~rc1-0ubuntu13 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/dmitriy/Desktop/cristiano_ronaldo_vs_dinamo__kiev_by_cronaldo7.wmv.
ASF file format detected.
VIDEO:  [WMV3]  640x480  24bpp  30.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 author: CRonaldo7
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
vo_xvmc: X-Video extension 2.2
vo_xvmc: No X-Video MotionCompensation Extension on :0.0
Error opening/initializing the selected video_out (-vo) device.


Exiting... (Quit)


```

---

### Post by Pulshion on 2007-10-28
bump

---

### Post by Gremlinzzz on 2007-10-28
try
sudo apt-get autoremove mozilla-mplayer
then go to home folder click view check show hidden files if you find a mplayer folder there delete it then
sudo aptitude install mozilla-mplayer

---

### Post by fannus on 2007-10-28
erp, responded to the wrong post :D

---

### Post by andrew.46 on 2007-10-31
Hi,

 I have a suspicion that there is a very simple solution to your problem:

> **Pulshion said:**
> [...]
vo_xvmc: X-Video extension 2.2
vo_xvmc: No X-Video MotionCompensation Extension on :0.0
Error opening/initializing the selected video_out (-vo) device.
Exiting... (Quit)
[/CODE]

To find out what video output is available to you type the following in a Terminal window:

```
mplayer -vo help
```

 I suspect that one of these will be xv, so try your video as follows:

```
mplayer -vo xv video_name
```

making the obvious substitution for 'video_name'. If this is successful you will need to adjust this setting in your ~/.mplayer/config file.

                     Andrew

---

