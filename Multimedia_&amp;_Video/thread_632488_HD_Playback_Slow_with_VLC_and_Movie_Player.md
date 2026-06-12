---
title: "HD Playback Slow with VLC and Movie Player"
date: 2007-12-05
forum: Multimedia &amp; Video
---

### Post by esc1 on 2007-12-05
Playback is slow to start and slow if it starts at all. Sound doesn't work on some as well. Any advice?

---

### Post by Cuppa-Chino on 2007-12-05
could you provide some system specs and what driver you are using for video?
thanks

---

### Post by esc1 on 2007-12-05
I have an xp 2500 mobile overclocked to 1.8ghz with half a gb ram dual channel.  I know the rams a little lacking but should still be able to handle it.

How do I go about checking my drivers?

---

### Post by Cuppa-Chino on 2007-12-05
Your cpu seems to be a bit overstretched to play HD video but it will also depend on your video card and driver:

Ok firstly whats your graphics card

in a console type **lspci | grep VGA** command for that it should look like mine

```
**-desktop:~$ lspci | grep VGA**
02:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7900 GT/GTO] (rev a1)

```

and then check in Gutsy under** Systerm-->Restricted Driver** what it says about your video driver

thirdly what encoding is your video format you are playing

and fourth:
open a system monitor via **System-->System Monitor** go to the resources page and start your video playback, check the cpu usage, if it hits 100% this will be the cause of the stutter (which might still be fixable via the graphics driver etc)

the recommendation I have seen for HD playback is AMD X2 4400+ 1gb ram so far but lets see, also if you can play HD in windows and not in Linux then it will because both ATI and Nvidia do not offer the same driver video acceleration in Linux as they do in Windows (yet hopefully)

---

### Post by esc1 on 2007-12-05
02:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]

Believe I'm using fglrx drivers.

I am using Feisty.

Resources split up with a little more going to VLC, but the rest with my XGL. Guess running the eye candy and playing a hd vid is too much.

---

### Post by Cuppa-Chino on 2007-12-06
I download the eve trinity trailers for a trial, 720p went ok (not great) on my machine but 1080p stuttered significantly -- one core cpu hit 100% repeatedly.

I have core 2 duo 6300 and geforce 7900gt 2gig ram, so I guess my software setup must not be perfect.....

anyone give me any pointers, I have had repeated trouble getting nvidia xvmc to work.

---

### Post by bsmith1051 on 2007-12-07
> **esc1 said:**
> I have an xp 2500 mobile overclocked to 1.8ghz
I think your system is much too slow for high-def video, especially the newer MPEG4 and h.264 formats.  Older MPEG2 might work, especially if you can get drivers for your ATI 9700 to provide hw assist; I don't think this works very well in Linux though.

If you were running Windows, however, you could upgrade your video card to one of the new DX10 cards since they can do massive hw assist on all high-def video formats.  I'm referring to the ATI 2400/2600 and 3800 series and the Nvidia 8400/8600/8800 series.  And, even on Windows, the software support is spotty, i.e., the most consistent way to use the hw assist on these new cards is to also buy the $100 Cyberlink PowerDVD Ultra software!

---

### Post by Devport on 2007-12-15
For me video playback ( H.264 ) is very slow too.

Athlon X2 3800+, nVidia GeForce 6600 GT

This is enough to playback my videos on gentoo while the cpu is idle - on ubuntu the cpu is at max speed when playing the same vids.

Edit : Please ignore my post - using totem-xine fixes the speed problem.

---

### Post by imtheguru on 2007-12-15
Use mplayer. Preferably from the command line, without the gui. If mplayer drops a lot of frames then  your hardware is getting overstretched.

Cheers.

---

### Post by shirilover on 2007-12-15
> **Cuppa-Chino said:**
> I have had repeated trouble getting nvidia xvmc to work.

Xvmc will only accelerate MPEG-2 in linux, at least for now.

---

### Post by talon95 on 2007-12-15
Just as a data point, my 3.2Gig P4 will play 720p MKV's (x264) smoothly, but not 1080p (cpu maxes out) with MPlayer.  X850Pro ATI card and the latest ATI proprietary drivers.

---

### Post by hsjC on 2008-03-24
This is my computer:

Dual Core Opteron OC'ed to 2.5GHz
3GB RAM DDR400
Ati X1900 AIW

I have 8.3 catalyst, hardy beta(8.04), no xgl installed, compiz + AIGLX

I can play 720p pretty well. But CPU usage averages around 70%. I noticed in system monitor, vlc doesn't really take a lot of cpu power, but xorg take like 30%+ more cpu power. Is there a way to reduce that?

BTW, whether eye candy enabled or not, fullscreen playback always seems a bit mosaic. Why?

---

### Post by elustran on 2008-04-16
> **hsjC said:**
> BTW, whether eye candy enabled or not, fullscreen playback always seems a bit mosaic. Why?
Try running your videos using openGL drivers.  Took me a while and much hairpulling to figure that little one out.

By the way, I thought I'd throw my 2 cents in here:

Linbox:
Athlon XP 3000
Radeon 9800 pro 128meg
1 gig DDR 400

Winbox:
core2 4400
nVidea 8600 256 meg
2 gig DDR2-800

The linbox stutters on HD content (not sure why I'm bothreing with it on my SD screen, but I have videos encoded in HD nonetheless) with 100% CPU usage.  The winbox doesn't, using maybe 20% of the CPU and 35 megs of memory.  Given that my winbox is maybe upwards of 4x as good in some areas as my linbox, shouldn't the linbox be playing the video, albeit at 80% cpu usage, or am I just oversimplifying?

Are there any workarounds anyone can think of?  Any way to dumb down post-processing, etc to reduce CPU usage, since I have more resolution in those videos than I need anyway?

---

### Post by aeiah on 2008-04-16
just for some comparison; ive got an amd64 x2 3800, 1 gig ram, nvidia 7800gt and i can play 720p and 1080p x264 just fine using mplayer in 32bit gutsy with compiz running. (although 1080p isnt true full resolution since my hdtv just outputs 720p, so its downscaled) 

i have threads=2 set in my mplayer config although i dont think its truly dual core decoding, but im guessing it uses the 2nd core for ac3 decoding. ive found mplayer to yeild the best results. xine works too but i get gaps in the audio occasionally which knocks it out of sync.

---

