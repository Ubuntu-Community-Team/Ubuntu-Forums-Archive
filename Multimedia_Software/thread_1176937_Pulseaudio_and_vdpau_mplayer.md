---
title: "Pulseaudio and vdpau mplayer"
date: 2009-06-02
forum: Multimedia Software
---

### Post by whitethorn on 2009-06-02
Hi,

I recently bought myself a new computer.  My Graphics card is a Nvidia gtx 275 (nvidia 180 driver installed).  I can't really seem to figure out how to watch videos well on my pc system.  My prefered video app is Mplayer.  

After having installed from medibuntu, I got really wierd performance issues.  At some time mplayer even told me my computer isn't fast enough. Which isn't really possible.  I then followed a howto and compiled mplayer.  Which didn't really bring much of a difference.  

I then realized the problem lies on the sound output, when I use pulse as my soundoutput in mplayer conf.  The video will run fine for a while, but after a bit the video slows down (audio runs normally) then the video will speed up catch up and slow down again.  If I use alsa, then I sometimes don't get sound because it says alsa device is busy.  At the moment I left the sound blank and mplayer uses oss.  Unfortunately, I can't hear anything else while it's running.  

I don't really know what else to do, I tried updating pulseaudio using a howto I found online (some guy had a personal rep) unfortunately skype wasn't working with it (seems libasound2 wasn't update as well).  Any1 have an idea, how I can video working?

---

### Post by warchief_ryan on 2009-06-02
If you don't get your answer here I suggest you goto #mplayer@irc.freenode.net, they will know.

---

### Post by psyke83 on 2009-06-02
[This]("http://ubuntuforums.org/showthread.php?t=1146319") thread details the same issue. I've mentioned the appropriate bug report in the thread, [bug #345627]("https://bugs.launchpad.net/bugs/345627"), though nobody seems to have listened ;).

---

