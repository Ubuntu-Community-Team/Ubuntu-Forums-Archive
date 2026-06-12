---
title: "Static sound new Hardy install notebook nvidia"
date: 2008-09-20
forum: Multimedia Software
---

### Post by cus4fun on 2008-09-20
Just bought a Compaq Presario CQ50-105NR for my son away at college. I've successfully installed Hardy. It's a dual boot with Vista Home Premium (how pretentious!). Everything works well except for the sound. It crackles. Kind of a static sound. It's as though the gain is turned up too far for the speakers... if that makes any sense. However, it works fine in Vista (gag). I apologize for my nooby-ness, but I'm trying!

Here are the specs from the HP support website:

Product Number   	FE872UA#ABA
Microprocessor 	1.90 GHz AMD Athlon X2 QL-60 Dual-Core Processor
Microprocessor Cache 	1 MB L2 Cache
Memory 	2048 MB
Memory Max 	Up to 3GB DDR2
Video Graphics 	NVIDIA GeForce 8200M
Video Memory 	Up to 895 MB
Hard Drive 	160 GB (5400 rpm)
Multimedia Drive 	LightScribe Super Multi 8X DVD±R/RW with Double Layer Support
Display 	15.4" WXGA High-Definition BrightView Widescreen (1280 x 800)
Fax/Modem 	High speed 56K modem
Network Card 	Integrated 10/100 Ethernet LAN
Wireless Connectivity 	802.11b/g WLAN
Sound 	Altec Lansing speakers
Keyboard 	101-key compatible
Pointing Device 	Touch Pad with dedicated vertical and horizontal Scroll Up/Down pad
External Ports 	

    * 3 Universal Serial Bus USB 2.0
    * 1 VGA (15-pin)
    * 1 RJ-11 (modem)
    * 1 RJ -45 (LAN)
    * 1 headphone-out
    * 1 microphone-in

Let me know what I need to supply to get help with a solution. The static isn't constant, it's only occasional when playing music or a movie or some such thing. Volume level doesn't make a difference except that when the static does occur, it's proportionately quieter or louder.

Thanks in advance,
Chris

---

### Post by alizais on 2008-09-23
I have the same problem. Mine is a Compaq Presario CQ50-115NR. People in different posts have mentioned fixing it with OSS but I have no idea how to do this.

Driver: Conexant High Definition SmartAudio 221 and NVIDIA High Definition Audio.

I have no idea why there are two drivers for this (as listed in Vista device manager) and I'm curious to know the answer.

Thanks for any help!

Edit: I searched some more and I found there indeed is a tutorial for installing OSS. Here it is:[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound) I'll be sure to write an update if my sound problem gets fixed or not. Wish me luck!!!
Edit: I tried the link above but it didn't work. Now sound doesn't play at all and KMix shows nothing. How do I get OSS to work?

$ osstest
Sound subsystem and version: OSS 4.1 (b rc1/200809240135) (0x00040090)
Platform: Linux/i686 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008


NOTICE! You don't have any audio devices available.
        It looks like your audio hardware was not recognized
        by OSS. Please contact 4Front technologies for help
        ([http://www.opensound.com/support.cgi](http://www.opensound.com/support.cgi)). Don't forget to
        include your soundon.log file to the support request.

---

### Post by Zaff on 2008-09-27
I have the same crackling static sound problem. It's a known issue that will be fixed in a later release of the kernel as stated here : [http://ubuntuforums.org/showthread.php?t=881363&highlight=sound+M3N78+pro](http://ubuntuforums.org/showthread.php?t=881363&highlight=sound+M3N78+pro).
Apparently newer HDA Nvidia sound chipset are not properly handled. I haven't been able to find a fix or a solution and I did try OSS4 but that only made things worse. I ended up reinstalling ubuntu completely because the only way I could get sound was by reinstalling the linux image at each boot. OSS4 removes the soundcore module (provided in the linux image) and for some reason I could never get it to stay put !
Let me know if you figure anything, I'd hate to have to buy a soundcard on top of this but I just might...

---

### Post by alizais on 2008-09-27
> **Zaff said:**
> I have the same crackling static sound problem. It's a known issue that will be fixed in a later release of the kernel as stated here : [http://ubuntuforums.org/showthread.php?t=881363&highlight=sound+M3N78+pro](http://ubuntuforums.org/showthread.php?t=881363&highlight=sound+M3N78+pro).
Apparently newer HDA Nvidia sound chipset are not properly handled. I haven't been able to find a fix or a solution and I did try OSS4 but that only made things worse. I ended up reinstalling ubuntu completely because the only way I could get sound was by reinstalling the linux image at each boot. OSS4 removes the soundcore module (provided in the linux image) and for some reason I could never get it to stay put !
Let me know if you figure anything, I'd hate to have to buy a soundcard on top of this but I just might...
I went to the link you posted and [iucoen ]("http://ubuntuforums.org/member.php?u=630729")had a response saying

> This has been fixed in the kernel tree:
[http://lkml.org/lkml/2008/8/4/110](http://lkml.org/lkml/2008/8/4/110)

This problem applies to all newer nVidia HDA chips.

Do you know if this is worth a try now that I've lost sound after installing OSS and removing ALSA?

---

### Post by Zaff on 2008-09-28
I don't think it'll solve your immediate problem which should be getting ALSA to work again. You need to get rid of everything oss installed. I got a big help out of the people at #ubuntu the other day but couldn't figure out how to keep the soundcore module from being deleted at each reboot. 
As to trying the kernel fix I don't even know how to do that but as soon as I figure it out, I'll let you know if it worked.

---

### Post by Zaff on 2008-10-03
I've patched the kernel with that fix mentionned earlier and it works (no more crakling). I've explained how I did it here : [http://ubuntuforums.org/showthread.php?p=5898266#post5898266](http://ubuntuforums.org/showthread.php?p=5898266#post5898266)
This will be fixed in Intrepid so I don't know if it's worth fighting for. After all the problem will be gone in a month.
But still.

---

### Post by hdhrnova on 2008-10-21
> **Zaff said:**
> I've patched the kernel with that fix mentionned earlier and it works (no more crakling). I've explained how I did it here : [http://ubuntuforums.org/showthread.php?p=5898266#post5898266](http://ubuntuforums.org/showthread.php?p=5898266#post5898266)
This will be fixed in Intrepid so I don't know if it's worth fighting for. After all the problem will be gone in a month.
But still.

perhaps.. but 8.10 has other issues on this laptop.  Right now (as to today) the nvidia 177.80 video driver is giving me grief.  With the new flash 10 update, firefox freezed every few seconds (even after video is completely downloaded to cache).  you can see the video do vertical redraws of the entire screen. The ath5k wifi driver losses packets and has low signal quality.   Network manager causes more problems with the wired interface.  

What all is broken??? I have no idea or where to start. Its all interrelated.

---

