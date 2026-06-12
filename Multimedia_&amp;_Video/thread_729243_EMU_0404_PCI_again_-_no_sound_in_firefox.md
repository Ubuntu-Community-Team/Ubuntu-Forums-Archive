---
title: "EMU 0404 PCI again - no sound in firefox"
date: 2008-03-19
forum: Multimedia &amp; Video
---

### Post by DragonlordP on 2008-03-19
I know this gets asked kinda often (I must have gone through most older threads) but my problem is a little different. I followed the instructions on this page: [http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga) and, while I couldn't make it at first, I finally got through the whole process. So, now I can play mp3s etc, but a) I can't get the sound to work on firefox (flash movies as in youtube etc) and b) I can't seem to get the card's left-right inputs to work.
Note that I run Hardy alpha 6 with the latest updates (I did it because I couldn't upgrade the alsa drivers on gutsy and hardy has 1.0.16 by default) and of course firefox 3 beta 4 (but I installed firefox 2 and it does the same thing, so I doubt it's that). I'm very new to linux, so it could be something very basic I missed.
Thanks, 
Panos

---

### Post by uBeer on 2008-03-27
I have the same sound card, but it's running fine here. I compiled and installed the driver, lib, firmware and utils in that order. I did no modprobes whatsoever. After that just restarted my system and everything worked.
What parts of that site did you actually do?

---

### Post by uBeer on 2008-03-27
Maybe I found a solution here: [http://ubuntuforums.org/showthread.php?t=686176](http://ubuntuforums.org/showthread.php?t=686176)

schnizzle said something about the order of the cards. Maybe that could be your problem. You could be able to fix this by disabling onboard AC'97 sound in the bios or maybe add a line to /etc/modprobe.d/alsa-base:
```
options snd-emu10k1 index=0
```
That way the card will always be the first one and according to schnizzle "stabilizes /dev/dsp for flash".

Hope this helps!

---

