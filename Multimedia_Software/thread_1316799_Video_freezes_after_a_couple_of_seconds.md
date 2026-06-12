---
title: "Video freezes after a couple of seconds"
date: 2009-11-06
forum: Multimedia Software
---

### Post by osced on 2009-11-06
I got a video problem, suddenly I can't watch any videos, when I start a video it freezes after a couple of seconds. I got that problem before & installed the mplayer for multi-threading & it solved it last time BUT for the moment I are using SMPlayer with MPlayer for multi-threading. I have tried VLC, totem & GXine and they doesn't seem to work either. I have tried the guide for Video on this forum.

I hope someone can help me solve this problem

//Osced
--------------------------
My PC specs:
OS: Ubuntu 9.10 [32 bit]
AMD X2 64 4400+
CPU: 2300 MHz
Motherboard: MSI K9VGM-V
Graphics: Nvidia GeForce 7800 GTX with Driver version 190.42

---

### Post by osced on 2009-11-06
Anyone having an idea ? I can't understand why the videos started to freeze, but I got this before, so maybe it's something I do who can creates that problem...

---

### Post by rvm4000 on 2009-11-06
Try to change the audio driver from alsa to pulse.

---

### Post by osced on 2009-11-06
Thanks for the answers, it looks like that fixed it for the avi files, I could watch through a video with no major problem. But for mkv-files it didn't work very good, instead of freezing I now got video lag and the audio comes before the video.

---

### Post by osced on 2009-11-07
I'm wondering if the problem is with the audio or the video, with the changing to pulseaudio the runs more smoothly , but it's still choppy. I know that I could watch with out problems on Tuesday & can't really see what changes I could do that would give this kind of error.

---

### Post by xc3RnbFO8P on 2009-11-07
Run VLC from Terminal.
> vlc

---

### Post by osced on 2009-11-07
VLC doesn't work, the audio is choppy, the output I got for vlc is: ```
QPainter::begin: Paint device returned engine == 0, type: 1 QPainter::begin: Paint device returned engine == 0, type: 1 [0x8d096a8] pulse audio output: No. of Audio Channels: 
``` I got a mplayer log that attach.  EDIT: I tested to use direct rendering and it looks like it works better, but still it looks choppy

---

### Post by rvm4000 on 2009-11-07
You may try to uninstall pulseaudio, and see if it works better. At least on Jaunty that fixed the problems of mplayer with alsa.

---

### Post by utkjamie on 2009-11-08
I'm having the same problems with audio being choppy with VLC and video freezing after a few seconds. The VLC audio problems started happening in Karmic beta but the video freezing seems to be fairly new.

---

### Post by osced on 2009-11-13
It seems to work some times, but not everyday, mainly it's the mkv-files who seams to stop after a while. I will try to reinstall pulseaudio, I hope that will work.
*[]("http://ubuntuforums.org/member.php?u=229350")utkjarmie* i have never really get VLC to work it seems to always be choppy, do you have tried some other mediaplayer?

---

### Post by utkjamie on 2009-11-14
> **osced said:**
> It seems to work some times, but not everyday, mainly it's the mkv-files who seams to stop after a while. I will try to reinstall pulseaudio, I hope that will work.
*utkjarmie* i have never really get VLC to work it seems to always be choppy, do you have tried some other mediaplayer?

KMPlayer seems to work sometimes, though the video freezes randomly and I have to skip forward or backward to get it going again. Plus, KMPlayer doesn't have as many features as VLC.

As for VLC, it seems to be mostly working now. I'm assuming more recent updates fixed it. It's still not perfect, though. Full-screen, for instance, doesn't cover the task bar -- but at least it seems to work okay for video.

I should probably point out that sometimes I have to shutdown Firefox and/or Seesmic to watch videos. Both seem to be memory and CPU hogs at times and that sometimes causes problems with watching video on my 1.6 MHz 1GB RAM laptop...

---

### Post by smitty65 on 2009-11-17
I found myself having the same video freeze ups in Mplayer and VLC.  I just updated to 9.10. The VLC player was always a bit jumpy but no freeze ups. I have all the latest updates.  This is my third edition with Ubuntu and I am very happy overall but still new--how do i change the audio driver?

---

### Post by osced on 2009-12-03
I have still these problems, it looks like I can se AVI-files without a problems but when I watch a mkv-files it got problem after a while and SMPlayer thinks that my computer is too slow. I got some weird problems sometimes when I watching stuff from the web, the whole video is sluggish both the audio and the video. That problem is randomly and I can't understand why I can see it somedays but not everyday

---

### Post by mr potatohead on 2010-01-26
I have an Asus m2 N68-am se2 amd duel core,  ubuntu 9.10 flash harddrive

when I play google video or youtube sometimes the video stops for maybe 10 seconds but the voice continues all of a sudden the video unlocks then speeds up until it syncronizes with the voice.  any one have a clue why this is happening?  I used to play around with redhad years ago this is so much better.

---

### Post by mr potatohead on 2010-01-26
I checked my video again and could not duplicate the problem.  then I remembered I installed the recommended driver which is the nvidia accelerated graphics driver(version185) it seems to work fine.

---

### Post by pickarooney on 2010-01-31
> **mr potatohead said:**
> I have an Asus m2 N68-am se2 amd duel core,  ubuntu 9.10 flash harddrive

when I play google video or youtube sometimes the video stops for maybe 10 seconds but the voice continues all of a sudden the video unlocks then speeds up until it syncronizes with the voice.  any one have a clue why this is happening?  I used to play around with redhad years ago this is so much better.

I have a similar issue - occasionally (once an hour or more) the video in an AVI file or youtube will freeze and the audio will continue. Only restarting the application (FF or smplayer) words to get around the problem.
This never happened in Jaunty. I'm using nvisia 185 drivers and pulseaudio in smplayer.

---

