---
title: "Playing video in terminal"
date: 2013-01-14
forum: Multimedia Software
---

### Post by sbcontt on 2013-01-14
Please don't ask me why. :-)
When I run mplayer -vo fbdev , it plays audio but no video, when I run sudo mplayer -vo fbdev, it plays video, but no audio. So I am using named pipe to start audio playback in a background terminal while video plays in current.
This however, effectively disables seek.
Also, attempting to ctrl^z or switch terminal during playback proves disastrous. The only way to safely get out of video seems seek out.
I do not know much about pipes. Currently I need to remove the 'used' pipe and create a new one each time.
I tried directfb and svga, but they led to system freeze.
I am posting this because I need advice. My current method is very restrictive. Can you suggest a cleaner and more functional way to play video in Ubuntu tty?

---

### Post by evilsoup on 2013-01-14
Have you tried just using `mplayer file`, leaving the program to determine what driver to use?

---

### Post by sbcontt on 2013-01-14
> **evilsoup said:**
> Have you tried just using `mplayer file`, leaving the program to determine what driver to use?

Yes I have, freezes the tty.
Sorry. Update: FATAL: Could not initialize video filters (-vf) or video output (-vo).
If it helps, my graphics hardware is NVidia and sound hardware is Creative X-Fi USB. As far as I know, NVidia releases driver only for x display, so perhaps I'll not be able to play HD videos in framebuffer anyway.

---

### Post by sbcontt on 2013-01-15
I have finally found the solution. Today I upgraded to the latest LTS and video playing is a lot more stable in it. The whole system is no more freezing due to a slight mistake with video playback. The worst that happens can be fixed by sudo kill -9 <bash PID>.
The audio-video problem was easily fixed with a chmod on /dev/fb0. Now mplayer plays both video and audio when I use -vo fbdev2 -vf scale=1366:768 parameter. I can also quit anytime using ctrl^z.

Mplayer is using ANSI characters to play the video if I do not mention any fb renderer.

---

