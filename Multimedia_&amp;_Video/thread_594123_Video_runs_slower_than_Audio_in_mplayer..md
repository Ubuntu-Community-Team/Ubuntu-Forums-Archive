---
title: "Video runs slower than Audio in mplayer."
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by tiachopvutru on 2007-10-27
Hi, I'm trying to play this mkv h264 file with 1280 x 720 resolution but the video runs slower than the audio. I have ATI proprietary driver installed from Restricted Driver Manager, and currently using mplayer.

It runs fine in Media Player Classic and CCCP codec pack from Windows XP. And I've heard that CCCP and mplayer use the same codec, and mplayer should gives a bit better result since its well... err, something is superior. (Don't know how to rephrase) And it's on the same machine so there shouldn't be any problem.

 When I open the file directly with mplayer (not running CLI), the video runs gradually slower than the audio. 
The default driver used is vx, and when I try gl or gl2 driver with the command **mplayer -vo gl -sid 0 file.mkv** or **mplayer -vo gl2 -sid 0 file.mkv**, the video runs significant slower (VERY slow). Also, when I run them and goes back to terminal, I see a message of "Your system is TOO slow to play this." I'm quite puzzled since I could run it fine in Windows on the same machine; it's only when I open the file directly (as in double-clicking) or running with gl or gl2 drivers that I receive problem.

I've heard of Xine and other frontend mplayers, but I want to solve this issue until or unless it's clear that I can't get around it...

Anyway, if someone can help me, thanks in advance.

The problem presents even when I disable Compiz-Fusion, btw.

EDIT:
I'm having problem with the video running 30 FPS, but the video doesn't lag behind for another video, with the same resolution, container, and video codec, but running 24 FPS

---

### Post by Supersaiyan.IV on 2007-10-27
> **tiachopvutru said:**
> Hi, I'm trying to play this mkv h264 file with 1280 x 720 resolution but the video runs slower than the audio. I have ATI proprietary driver installed from Restricted Driver Manager, and currently using mplayer.

It runs fine in Media Player Classic and CCCP codec pack from Windows XP. And I've heard that CCCP and mplayer use the same codec, and mplayer should gives a bit better result since its well... err, something is superior. (Don't know how to rephrase) And it's on the same machine so there shouldn't be any problem.

 When I open the file directly with mplayer (not running CLI), the video runs gradually slower than the audio. 
However, sometime, they audio and video are in sync when I run in CLI with **mplayer vid file.mkv**.  The default is the vx driver, and when I try gl or gl2 driver with the command **mplayer -vo gl -sid 0 file.mkv** or **mplayer -vo gl2 -sid 0 file.mkv**, the video runs significant slower (VERY slow). Also, when I run them and goes back to terminal, I see a message of "Your system is TOO slow to play this." I'm quite puzzled since sometime using **mplayer vid file.mkv** runs fine(although running through this sometime doesn't help either), and I could run it in Windows on the same machine; it's only when I open the file directly (as in double-clicking) or running with gl or gl2 drivers that I receive problem.

I've heard of Xine and other frontend mplayers, but I want to solve this issue until or unless it's clear that I can't get around it...

Anyway, if someone can help me, thanks in advance.

The problem presents even when I disable Compiz-Fusion, btw.

I have the latest 8.42.3 ATI driver, and had a similar problem today. The solution is worked out for VLC only, because mplayer complains with remaining low framerates.

Enable OpenGL output in VLC, and turn off compiz ($metacity --replace), then after you've watched the movie, change back ($compiz --replace). I hope you have DRI enabled.

peace

---

### Post by tiachopvutru on 2007-10-27
I don't want VLC though, since it has bad Softsub support.

---

### Post by tiachopvutru on 2007-10-28
<bump>

---

### Post by tiachopvutru on 2007-10-28
<bump>

---

### Post by tiachopvutru on 2007-10-28
<bump>

---

### Post by tiachopvutru on 2007-10-29
<bump>

---

### Post by spellprider on 2007-11-19
Try enabling frame dropping in video options of mplayer.

---

### Post by shirilover on 2007-11-19
Do you have the processing power to play high resolution H.264 video?
Hi-res H.264 streams require significant CPU to play smoothly, and even more so with soft-subs.
Even so, you can try to add the follwing switches to mplayer:

```

-framedrop -lavdopts fast:skiploopfilter=all

```

---

### Post by tiachopvutru on 2007-11-20
I installed SMPlayer and it pretty solve my problem. I notice though, that sometime I see the noticeable diagonal line run from top right to lower left as if it doesn't process frame fast enough. I believe my PC to be enough to play those videos since I was able to play those fine back in Windows XP.

Switching driver from xv to gl or gl2 eliminates the sort-of line that kinda appear on occasions but for videos with high res, the video lags behind again...

It's probably something about my clock speed though. I notice my CPU runs 100% when I look on System Monitor.

---

### Post by Supersaiyan.IV on 2007-11-22
<bump>

---

### Post by wladyx on 2008-01-27
bump

---

### Post by rvm4000 on 2008-01-28
I read **gl2:yuv=3** is faster than **gl2** alone. Try that.

---

