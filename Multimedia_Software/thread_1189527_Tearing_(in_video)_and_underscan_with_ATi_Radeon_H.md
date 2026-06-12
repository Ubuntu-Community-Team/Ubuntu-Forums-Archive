---
title: "Tearing (in video) and underscan with ATi Radeon HD 4350"
date: 2009-06-16
forum: Multimedia Software
---

### Post by armitage1337 on 2009-06-16
Hi,

I recently purchased an ATi Radeon HD 4350 graphics card for use with an HTPC (a Sony VAIO RC110G) running Kubuntu 9.04 that I've got hooked up to my HDTV. I've run into a few issues with it:
1. The open source RadeonHD drivers aren't working with **HDMI audio output**. If this can be fixed, the next 2 problems might be irrelevant.

2. When **playing a 720p MKV video** in SMPlayer in full screen, I quite a bit of **tearing**. I tried using```
sudo aticonfig --sync-vsync=on
```and```
sudo aticonfig --sync-video=on
```but neither seemed to make any difference. I'm not sure if this was a problem with the default (RadeonHD) drivers.

3. There is a substantial amount of **underscan** (2"-3"), even though I have the resolution set to 1080p (the resolution of my HDTV). This wasn't an issue with the default (RadeonHD) drivers.

Thanks in advance for the help!

---

### Post by usererror on 2009-06-23
I just picked up this card from slickdeals, should be here by Monday.  Did you get your issue fixed?

---

### Post by sanumala on 2009-06-24
> **usererror said:**
> I just picked up this card from slickdeals, should be here by Monday.  Did you get your issue fixed?

Hi there

Dont use ATI cards in ubuntu. They are not goona work i have wasted $200 USD for ATI Radeon 4850 512MB long back. I have tried all possible soultions but nothing worked out.

Finally I am back to nvidia 9800 GT 1GB.

---

### Post by Laysan_A on 2009-06-24
I'm having a terrible problem with tearing using ati's driver fglrx. Every object on my desktop and/or video screen tears clear across the screen - except while the screen loads, when it momentarily clears.

Unfortunately the open source ati radeon drivers don't do so well with streaming video in full screen (forget about 3D games).

I tried the 8-something fglrx from the repositories and the 9-5 from ati, and neither worked. For this issue alone, I wish I had stuck with Intrepid for a while longer.

There is a bug report, but not much activity here
[https://bugs.launchpad.net/fglrx/+bug/303697](https://bugs.launchpad.net/fglrx/+bug/303697)

I have always had ati, and the fact that ati and amd are now together is a good thing for linux, but I have to agree with sanumala, for the time being at least - go with nvidia if you want it to work.

Oh, there is something you might want to try (I haven't done it myself). Someone has compiled the ati drivers for intrepid to work on jaunty. If you want to give it a go, here's the link:
[http://www.kdedevelopers.org/node/3942](http://www.kdedevelopers.org/node/3942)

---

### Post by armitage1337 on 2009-07-07
> **usererror said:**
> I just picked up this card from slickdeals, should be here by Monday.  Did you get your issue fixed?

I ended up using Arch Linux and the proprietary Catalyst drivers, and they work for the most part. The only aspect in which they are lacking is performance: 1080p video playback results in tearing (though 720p works just fine).

> **sanumala said:**
> Hi there

Dont use ATI cards in ubuntu. They are not goona work i have wasted $200 USD for ATI Radeon 4850 512MB long back. I have tried all possible soultions but nothing worked out.

Finally I am back to nvidia 9800 GT 1GB.

I would have used an NVIDIA card (and actually did buy one first and then ended up returning it), but the NVIDIA cards don't have built in audio chipsets; they instead require you to connect your motherboard's S/PDIF output header to the graphics card so that it can pass audio through to the HDMI port along with the video. The VAIO RC110G doesn't have an S/PDIF output header on its motherboard and I didn't want to mess with buying a PCI sound card to get an S/PDIF output header, so I settled for an ATi card.

Hopefully the RadeonHD driver will improve in the future (IIRC, they were missing HDMI audio output support) to the point that I can use it instead and get fully functional 1080p playback.

---

### Post by davea88 on 2009-11-18
Running Ubuntu 9.10 with a new HD4350 (system with no fans,
uses heat pipes and Zalman aluminum case)
(Nov 2009) and not only do some areas tear off to the right
(mostly red lines) but some menu grey areas have a scintillating
bunch of tiny blue and red dots.  Ugh.  Dell 2005FPW
monitor. Running standard ubuntu driver, I tried ATI
stuff briefly and it did not seem to help.  And with 9.04
the ATI non-open drivers did not work at all, it seemed. X died.
So had to use the stock Ubuntu drivers there.
Suggestions?

---

### Post by xzero1 on 2009-11-18
Have you tried this sync option with mplayer's opengl output?

mplayer -vo gl ....

BTW, the 4350 should support hardware video acceleration which on my 4770 is virtually tear free.

If you are not afraid of getting your hands dirty by compiling stuff and are lucky see this thread: [http://www.phoronix.com/forums/showthread.php?t=19983]("http://www.phoronix.com/forums/showthread.php?t=19983")

---

