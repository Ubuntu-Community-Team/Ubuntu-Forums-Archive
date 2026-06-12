---
title: "smooth hd playback"
date: 2008-11-28
forum: Multimedia Software
---

### Post by bharath1097 on 2008-11-28
I am trying to play 1080p hd content on my laptop smoothly. My processor is 1.4ghz core2duo. I know its very weak but in windows xp using media player classic and ffdshow or vlc i was able to play 1080p hd videos smoothly. But in ubuntu i have tried everything and i am not able to get smooth playback. I tried mplayer,vlc,tote-xine,totem-gstreamer,kaffeine everything. When i check the cpu usage in windows both the cores are being utilized heavily and i am getting smooth playback. While in ubuntu one core is maxed out while the other core is not being utilized at all.Strangely vlc in windows is utilizing both cores while linux vlc is utilizing one core. I changed the xine settings and set ffmpeg thread count=2 and disabled postprocessing, i used threads=2 argument for mplayer but whatever i try i am unable to get playback using 2 cores and 1.4ghz single core is simply not enough for 1080p h264 playback.

---

### Post by djbon2112 on 2008-11-28
I've had the same problem also. 2.0 GHz Core 2 Duo laptop. I got so fed up I just ended up getting all my HD in 720p instead of 1080p because that's all that would play! Tried recompiling mplayer for multiple cores also but it didn't work.

---

### Post by cor2y on 2008-11-28
In all three major OS for hidef 1080p playback a 1.4ghz dual core is not going to work  .
Until the video drivers in linux are improved to match whats in windows you need at least a dual core 2.8ghz for smooth 1080p playback (dual core 2.0ghz can handle 720p)
Even in windows you need at least a 2.5ghz with a modern video card for smooth 1080p playback, by modern i mean one that specifically states it can do hidef video playback like any nvidia from 8600gt and above or one of the X1250XT and above ATI cards on board video for laptops that aren't of those chipsets won't be able to do smooth 1080p playback .

---

### Post by djbon2112 on 2008-11-28
> **cor2y said:**
> In all three major OS for hidef 1080p playback a 1.4ghz dual core is not going to work  .
Until the video drivers in linux are improved to match whats in windows you need at least a dual core 2.8ghz for smooth 1080p playback (dual core 2.0ghz can handle 720p)
Even in windows you need at least a 2.5ghz with a modern video card for smooth 1080p playback, by modern i mean one that specifically states it can do hidef video playback like any nvidia from 8600gt and above or one of the X1250XT and above ATI cards on board video for laptops that aren't of those chipsets won't be able to do smooth 1080p playback .

No you don't. My laptop does 1080p perfectly in Windows XP (2.0 GHz Core 2 Duo and a non-HD processing video card), but in Linux it's painful.

---

### Post by bharath1097 on 2008-11-29
> **cor2y said:**
> In all three major OS for hidef 1080p playback a 1.4ghz dual core is not going to work  .
Until the video drivers in linux are improved to match whats in windows you need at least a dual core 2.8ghz for smooth 1080p playback (dual core 2.0ghz can handle 720p)
Even in windows you need at least a 2.5ghz with a modern video card for smooth 1080p playback, by modern i mean one that specifically states it can do hidef video playback like any nvidia from 8600gt and above or one of the X1250XT and above ATI cards on board video for laptops that aren't of those chipsets won't be able to do smooth 1080p playback .
My 1.4 ghz dual core was able to play 1080p video perfectly in windows xp using mpc and ffdshow. I dont have a nvidia or ati video card. I have intel gm965 onboard graphics which does not accelerate hd. In linux only i was not able to have smooth playback. "In windows ffdshow is utilizing both the cores while in linux all video players were able to use only one core". Clearly 1.4ghz single core is not enough to play hd. But ffdshow was able to give smooth playback by utilizing both the cores.

---

### Post by Romu on 2008-12-22
Hi all,
A little up for this thread because I'm interested in such a discussion.

My configuration is :
- Hardy 64 bits
- Macbook Pro Core 2 Duo 2, 16 GHz
- 2 GB of RAM (DDR 667 MHz)
- HDD 120 GB at 5400
- ATI x1600 "Full Speed" with 128 MB of memory (ATI driver from the Hardy repository)

I tried 2 HD videos (720p), both played with Totem (GStreamer I guess), with different results :
- one is an XVid video with DD sound track, played smoothly without any problem,
- one is MPeg4 with AAC sound track, pretty unwatchable, with a little freeze every 2 seconds.

So I would like to know if this is a well know issue ? And if there is some fixes, or well know settings to remove this limitation ?

Thanks in advance.

---

### Post by rainbowmagik on 2008-12-24
CPU: 2.66x4 (intel)
Ram: 2 gb
gfx: nvidia 8800GS

HD plays fine in windows. In ubuntu though, it stutters on scenes with too much going on.

Only the fourth core seems to be used by my player, the stuttering occurs when it reaches %100.

So I will try to get it to use the other three, and post my results.

Any help with this is most welcome.

---

### Post by KhaaL on 2009-02-16
it seems that the only solution is to compile mplayer with support for coreAVC according to this article: [http://www.zimbio.com/Ubuntu+Linux/articles/524/1080p+HDTV+H+264+Playback+Linux](http://www.zimbio.com/Ubuntu+Linux/articles/524/1080p+HDTV+H+264+Playback+Linux)

But surely there is another alternative to this...?

---

### Post by techathy on 2009-03-13
An intresting read, I'm playing 1080p material with a basically out-the-box intrepid install on my desktop: 
Pentium Dual Core E5200 (2.5GHz Wolfdale)
4GB PC2-8500
Asus P5Q WS
Radeon X600 Pro
In fact I can down-clock to 1.73GHz before it starts to drop frames, but how does that relate to the mobile C2D processor line?

EDIT: 
I should add that to get smooth playback I need to use a non-composing window manager. With a composing window manager the CPU needs to be 2.26GHz for visually smooth playback.

---

