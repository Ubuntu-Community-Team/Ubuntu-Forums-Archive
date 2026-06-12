---
title: "Flash hw acceleration issues on *some sites"
date: 2011-04-25
forum: Multimedia Software
---

### Post by TomFumb on 2011-04-25
Sorry for typing up yet another flash video type issue but I'm not able to find the answer for my problem.

I have a Zotac maghd-nd01-u (32-bit dual-core Intel Atom 330, NVIDIA ION graphics) with Ubuntu 10.10 installed and used primarily for XBMC (great stuff!), all desktop effects disabled.

I have the NVIDIA drivers Ubuntu offered me when I first installed (early April 2011) - version 260.19.06, which I believe is correctly configured for hw acceleration ("glxinfo | grep -i direct" gives "direct rendering: Yes"). I'm pretty sure this is all OK as I can get smooth playback on 1080p video in XBMC.

However Flash player (10.3.181.5, updated via Flash-Aid) doesn't seem to work with hw acceleration on some sites. I can watch a 720p video on Youtube in full screen without a problem, but other lower resolution video scaled up to full-screen pins the CPU and gives about 10 fps (e.g. CBC hockey [http://www.cbc.ca/video/#/Sports/Hockey/Highlights/1619393395/ID=1896254284](http://www.cbc.ca/video/#/Sports/Hockey/Highlights/1619393395/ID=1896254284) (link might not last forever)).

Flash-Aid already took care of setting OverrideGPUValidation in flash player's /etc/adobe/mms.cfg and this is still an issue. Checking / un-checking 'Enable Hardware Acceleration' doesn't seem to make a difference. I'm not sure where to turn. Any suggestions?

---

### Post by lovinglinux on 2011-04-25
The problem is that the content needs to be compatible with hardware acceleration. YouTube is one of the sites that works well when you use the OverrideGPUValidation, but if the site doesn't provide a decent flash video player, then I am afraid there is nothing you can do about it. However, I have tested the link you provided and although it uses twice as much CPU than YouTube on full screen, it plays smoothly on my machine with Core 2 Duo and nVidia 7300GT.

I am not using Compiz, but I use Kwin. Perhaps you could turn off visual effects and check if gives you a better performance.

---

