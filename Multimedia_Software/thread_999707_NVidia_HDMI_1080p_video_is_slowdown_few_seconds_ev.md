---
title: "NVidia HDMI 1080p: video is slowdown few seconds every few minutes"
date: 2008-12-02
forum: Multimedia Software
---

### Post by Arrouan on 2008-12-02
Hi,

My issue is that all videos (quicktime, xvid, divx, x264) play almost well but every few minutes, the video slow down (it is like if the movie go from 25fps to 20fps) during few seconds (maybe 10) and then everything go back to normal.

It is the most noticeable with HD movie (720p and 1080p).

I try with Ubuntu 8.04 and KUbuntu 8.10 and I still have the problem.

My configuration is DualCore2 3.2Ghz (Intel) 4Go RAM and GeForce 9500GT.
I have two display one lcd screen samsung 16/10 22" on DVI (primary screen) and a HD TV Samsung 37" 1080p 60Hz on HDMI (secondary screen).

My xorg is setup to use 2 different X and xinerama (setup done with nvidia-settings).

I tweak xorg.conf manually to use compoment 1080p.

I also try the last beta/non-beta nvidia driver from their websites (and of course the ones package with ubuntu).

I also try with vlc, mplayer, kaffeine(xine). And all the players have the same issue.

Does anyone have the same error or an idea how to fix it ?

Thanks.

---

### Post by Arrouan on 2008-12-02
Anyone know if a long hdmi cable can do this issue.

because my tv is connect through a 5 meter hdmi cable to my computer.

---

### Post by MarcellusBR on 2009-03-30
Hi Arrouan

I was having the very same problem connecting my HP Pavillion Notebook to my Sony Bravia 46" trough a HDMI Monster Cable.

Even the 720p videos had it. A FPS slowdown every minute, especially in complex scenes, with lots of colors and objects in motion.

My notebook has a Nvidia GeForce Go 7600, with 128MB of memory.

I didn't find a peremptory solution, but a manage to find a very effective answer. Trough the video card's control panel, i set up the video playback configurations to show images only on the Sony Bravia HDTV. The notebook's monitor turns off, and the videos played in the TV (with WMP, VLC, Goom, MPC, etc), with every codec (Xvix, H264, Divx, MKV) plays smooth and with almost no reduction of the FPS during the whole time. Even with the 1080p videos.

I was very relief by discovering that, after hours of searching in the internet.

So i hope this will help you too and other people who sees this and have the same problem.

By the way, sorry for the bad grammar.

:lolflag:

Good luck!

---

