---
title: "HD video playback on 13.10 is lagging as hell"
date: 2014-02-04
forum: Multimedia Software
---

### Post by zemko on 2014-02-04
Hi, since I updated to 13.10 in december (previously I used 13.04) I have problems with HD video playback (720p, 1080p) and some 480p .mkv files. I am using Smplayer. On 13.04 there were no problems. I tried purge smplayer and install it again, I tried to set CPU at maximum when playing, I tried fresh start...nothing helped

For example: 40 minutes long video lags every five minutes cca, syspeek shows maximum CPU usage, but only the video is lagged, every other programm is working fine (chrome, skype...)

I have Lenovo B560 with Intel HD card, @2.6GHz, 8GB RAM. On 13.04 I had Intel Graphics installer (source: [https://01.org/linuxgraphics/downloads/2013/intelr-graphics-installer-1.0.2-linux](https://01.org/linuxgraphics/downloads/2013/intelr-graphics-installer-1.0.2-linux)), but this one is not suppported on 13.10, and what I saw in some articles, 13.10 should contain newest drivers.

Any suggestions? Thanks in advance

---

### Post by SeijiSensei on 2014-02-04
You can try a couple of alternative video drivers and see if they help.  I rarely use Intel video; most of my desktop machines have NVIDIA or ATI graphics.  If the Intel card supports OpenGL, you can try that driver in SMPlayer instead of the default xv driver.  Go to Options > Preferences > General > Video and try the fast GL driver. Then look at Preferences > Performance and see how many threads you are using.  Perhaps using 2 or 4 threads might help.  Other settings like the loop filter can matter as well.  Try some different combinations and see if any of them work for you.

---

### Post by zemko on 2014-02-04
@SeijiSensei oh good point, I tried something but "only" result is that the lags are "smoother" and the gap between them is longer (from 9 to 13 minutes when watching 720p video)

---

