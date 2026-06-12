---
title: "Ubuntu 10.10 vlc HD (mkv) Lag"
date: 2010-10-30
forum: Multimedia Software
---

### Post by Kyluke on 2010-10-30
Hey guys I have a fresh install of ubuntu 10.10 x86_64 installed on my laptop.
My problem is some epic lag when playing HD files in vlc namely, mkv files.
Specs:

CPU: 2.2Ghz Dual Core AMD
GPU: ATI HD3200 256mb (Open Source Driver)
RAM: 3GB

I do have compiz running, switching to metacity does nothing. I have changed the buffering value in vlc and the usual of VSync settings etc etc.

Is there something I am missing, or is this a new problem?

(My system can play 22Gb mkv files no problem in opensuse and windows so I was just wondering how to fix this in ubuntu)

---

### Post by P4man on 2010-10-30
YOu can fix it by installing an nvidia card that supports VDPAU :)

I have no idea how opensuse does it, afaik there is no h264 decode acceleration for ATI cards under linux and at 22GB per movie, I imagine your cpu cant do it purely in software.

---

### Post by Kyluke on 2010-10-31
I cannot install a nvidia card into my PC as it is a laptop.

How do I fix the lag?

---

### Post by P4man on 2010-10-31
If it is what I think it is, that with videos with very high bitrate the cpu cant keep up and drops frames (so its not audio lag or something?) then there isnt much you can do. You could try another mediaplayer like smplayer, but 22GB per movie is huge and pretty much the same as the original bluray, and AFAIK need at least 3 GHz dualcore AMD to decode that in software, or have GPU decode.

So basically you need to buy another laptop, run windows (ATI drivers do support h264/VC1 etc decode on windows, just not on linux) or recode your video to lower bitrates.

---

### Post by Kyluke on 2010-11-02
so i can't watch HD movies in ubuntu? even 4gb files lag

---

### Post by P4man on 2010-11-02
At 4GB per movie, Id expect your CPU to be able to do it in software. Perhaps you should try to narrow the problem down a bit, try different players (SMplayer, movieplayer) and different video's and find a pattern.

---

### Post by fonsi2099 on 2010-11-20
the same problem for me!! so I can't watch HD movies in ubuntu 10.10? 
CPU: 2.8 Ghz Dual Core AMD 64Bit
GPU: ATI HD3400 500MB ( AMD propietary Driver)
RAM: 3G

Please you will find a way, like always :P
Many thanks

---

### Post by cchhrriiss121212 on 2010-11-20
It is possible to use hardware acceleration with ATI cards:
[http://art.ubuntuforums.org/showthread.php?t=1588465](http://art.ubuntuforums.org/showthread.php?t=1588465)

---

### Post by livingreality on 2010-11-28
I have the exact same problem with VLC lagging and the same specs except that i have and ATI Radeon HD3400 

This problem appears since upgrading to 10.10

I did not have this problem whatsoever in 10.04

---

### Post by Kyluke on 2010-11-28
i have found that the opensource drivers are much better for this sort of thing. i only use the open source drivers, no more tearing, suspend and hibernate work flawlessly and my HD films play without a hitch. so i suggest using the open source drivers, the only problem i have with them is that my battery lasts half an hour less but other than that they are better than the proprietary drivers

---

### Post by Eugenian on 2010-12-28
> **livingreality said:**
> I have the exact same problem with VLC lagging and the same specs except that i have and ATI Radeon HD3400 

This problem appears since upgrading to 10.10

I did not have this problem whatsoever in 10.04

My mkv/vlc problem (audio track plays but no video) began after upgrading to Ubuntu 10.10. I solved the problem by upgrading from VLC 1.1.4 to VLC 1.1.5, following the instructions here:

[VLC 1.1.5 is released! PPA Ubuntu & LinuxMint | Unixmen]("http://www.unixmen.com/software/1304-vlc-115-is-released-ppa-ubuntu-a-linuxmint") 

(Dell D600, 32-bit, with a Radeon Mobility 9000 32MB card.)

---

### Post by Isterklister on 2011-03-14
I'm a little bit late but I hade the same problem with mkv files. I have also ATI video card and I uninstalled the driver from ATI and use the open source version (I also use VLC 1,1.7) and now I can play the MKV files without lags.

---

### Post by fonsi2099 on 2011-03-15
I've resolve the problem, I'm using VLC 1,1.7 and now I can play the MKV files without lags. :popcorn:

---

