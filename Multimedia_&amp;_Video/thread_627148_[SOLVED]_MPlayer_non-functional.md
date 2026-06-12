---
title: "[SOLVED] MPlayer non-functional"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by Bheegerji on 2007-11-29
Not able to play video files in MPlayer. 

"Error opening/initializing the selected video_out (-vo) device." is the message that I get when i try to play video files in MPlayer.

No probs with VLC media player or Totem Movie player.

---

### Post by shirilover on 2007-11-29
Have you tried using -vo xv or -vo gl?
If you're using the GUI, run gmplayer and then open the preferences and choose the video output from there.

---

### Post by Bheegerji on 2007-11-29
> MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 4, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Can't open preferences.

---

### Post by logos34 on 2007-11-29
look for **gui.conf** file in $HOME/.mplayer.  'vo_driver =' is second line

---

### Post by Bheegerji on 2007-12-01
Thanks guys, I changed the vo driver from xv to gl in the config.gui. And MPlayer performs like a pro.

---

