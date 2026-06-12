---
title: "Speeding up choppy video playback"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by botulismo on 2007-05-29
I have this problem with all video players it seems. My computer should be able to handle video playback pretty well, considering, but I rarely get non-frame-skipped video playback, especially in full screen. My hardware is as follows: Athlon 64 3500+, 2.5GB of Ram, 250GB HD, Radeon x200 integrated graphics that steals 128 mb from the 2.5 GB. Running Ubuntu 7.04. I do have Beryl/XGL running but the problem happens regardless of whether it's on or not.

I would think my computer would be able to play a video pretty well, considering I had a 500mhz Pentium with Windows 98 back in the day (don't even remember what kind of video card it was in particular but I know it was an S3) that could software-decode DVDs in fullscreen better than my computer can.

I know in Windows the DirectX video acceleration can make all the difference in the world sometimes. Is there a way to do this with OpenGL, and if so, has someone already done it and made it effective? 

Also, is this just due to ATI and their Linux drivers? Essentially, no matter how powerful my system, I'll never be able to play a full-framerate DVD video as long as I insist on using the card that's included?

This is really my only true complaint about Linux. Ever since I've been running it (across distros), video playback has been very poor, but hey, I can always encode what I want to watch to DVD and play it while sitting on the couch - more comfortable anyhow.

---

### Post by tgm4883 on 2007-05-29
Do you have your video card drivers installed?

post the output of this from the terminal

```
glxinfo | grep direct
```

---

### Post by RTrev on 2007-05-29
I'm having very much the same problem, and I have a dual-core AMD 3800+ and 2G of RAM, plus an Nvidia GeForce 7300 GT with its own 512M of RAM.  I have the restricted Nvidia driver running.

Seems like it aught to work!

My wife suggested that I make sure DMA was enabled for my DVD drive, and it appears to be.  Both the BIOS and hdparm say it's got DMA enabled.

And per the earlier suggestion:

```

bob@ubu32:~$ glxinfo | grep direct
direct rendering: Yes

```

If you find an answer, please post back.  I'm out of ideas.  Thanks...

---

### Post by Canis familiaris on 2007-06-22
I have the same problem but no hope to solve it because I have SiS Video card whose drivers are extremely buggy. But  you can try GeeXbox which due to its dedicated multimedia will play DVDs perfectly.

---

### Post by RTrev on 2007-06-22
> **Anurag_panda said:**
> I have the same problem but no hope to solve it because I have SiS Video card whose drivers are extremely buggy. But  you can try GeeXbox which due to its dedicated multimedia will play DVDs perfectly.

Never heard of it.  I'll look it up..  Thanks!

Bob

---

### Post by _profox on 2007-06-22
There are multiple things to consider regarding video playback - I will outline a few important things:

1. Make sure your video card is able to accelerate the video (glxinfo|grep direct will always return No in Xgl though! this is because of the way Xgl (Xglx) works)

2. Use the "xv" video driver in your movie player. Xv aims to use the 2D acceleration from your video card to render the video. It is the best choice in most circumstances. (note: AIGLX users might experience problems with Xv; hopefully this will be solved in future AIGLX implementations)

3. Otherwise, try the "gl" or "gl2" video driver in your movie player. Like you said, this method will render the video using OpenGL. (the same note as above for AIGLX users though!)

4. X11/Xshm is another solution.. But often the performance is worse, and it is software based. I do mention it though because it is the only solution that really works well with AIGLX right now. (note: smplayer or mplayer [console version] can stretch the video with a decent quality when using X11/Xshm, so those are preferred when you're stuck on X11/Xshm)

5. Some movie players provide functionality to reduce choppy video playback (like mplayer) with options like "-framedrop" okay, frames will be skipped (dropped) but the video will still look pretty smooth and the audio will try to keep in sync, all in all it does reduce choppiness as we know it.

6. Like was said, try playing a video on your hard drive - the problem might be caused by your DVD drive.

And finally, a personal note: I have the opposite experience concerning video performance. Video performance has always been better on linux than windows on my machines. Video cards in my machines: NVidia Geforce 3 ti200 with nvidia-legacy driver; ATI (AMD) Mobility Radeon X700 with fglrx driver; ATI (AMD) Mobility Radeon 7500 with radeon+dri driver; Intel GMA 915 with intel+dri driver.

Also: the fact that a powerful video player like mplayer can do so much to improve the playback speed in certain circumstances has helped me to watch HD video on an old radeon 7500 / 800Mhz laptop - in reduced quality and by using special options that can cause occasional visual glitches though - but it did work and I wasn't able to watch HD video at all in Windows because the machine itself was just too slow.

---

### Post by Canis familiaris on 2007-06-22
> **RTrev said:**
> Never heard of it.  I'll look it up..  Thanks!

Bob
VIsit here to know more abut GeeXboX

[http://dogbuntu.wordpress.com/2007/06/06/geexbox-the-ultimate-home-jukebox/]("http://dogbuntu.wordpress.com/2007/06/06/geexbox-the-ultimate-home-jukebox/")

---

### Post by Canis familiaris on 2007-06-22
> **_profox said:**
> 
And finally, a personal note: I have the opposite experience concerning video performance. Video performance has always been better on linux than windows on my machines. Video cards in my machines: NVidia Geforce 3 ti200 with nvidia-legacy driver; ATI (AMD) Mobility Radeon X700 with fglrx driver; ATI (AMD) Mobility Radeon 7500 with radeon+dri driver; Intel GMA 915 with intel+dri driver.

Also: the fact that a powerful video player like mplayer can do so much to improve the playback speed in certain circumstances has helped me to watch HD video on an old radeon 7500 / 800Mhz laptop - in reduced quality and by using special options that can cause occasional visual glitches though - but it did work and I wasn't able to watch HD video at all in Windows because the machine itself was just too slow.

In what way did you configure MPlayer?

---

### Post by _profox on 2007-06-22
> **Anurag_panda said:**
> In what way did you configure MPlayer?

I compiled a fresh compile from svn.
To be able to play a HD video in lower quality I just experimented with what mplayer told me.
Something like this:
*-framedrop -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all*

---

### Post by SyberKowboy on 2007-07-11
I'm having loads of problems with full screen vids. Doesn't really matter the compression type or codec. I too am using Beryl with glx. for a while I had no video at all or only sometimes, then I reinstalled some codec pack and I can play them in a window just fine. The weird thing is that when this installation of Ubuntu (Breezy) was fresh it played the same videos full screen with VLC no problem. I don't know enough to use the 'vx' or 'gl'. Please advise.  Thanks,

---

### Post by svega85 on 2007-08-07
> **_profox said:**
> I compiled a fresh compile from svn.
To be able to play a HD video in lower quality I just experimented with what mplayer told me.
Something like this:
*-framedrop -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all*


ok i had this same problem cuz i compiled from svn too. there is a bug in the sound driver that makes video slow. the way i fixed it is 
if you have a gui right click open preferences click audio tab select oss driver
if you dont have gui than start mplayer with 
mplayer -ao sdl

---

### Post by mocha on 2007-10-20
> **svega85 said:**
> ok i had this same problem cuz i compiled from svn too. there is a bug in the sound driver that makes video slow. the way i fixed it is 
if you have a gui right click open preferences click audio tab select oss driver
if you dont have gui than start mplayer with 
mplayer -ao sdl

Sorry to raise this from the grave, but I've always had problems with choppy video under Ubuntu.  I just tried your suggestion and TADA, it's not choppy anymore!  Thanks!  I've been looking for a solution for 4 months!  Who would've thought an audio problem would cause a video issue..

---

