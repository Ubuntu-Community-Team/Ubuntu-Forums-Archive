---
title: "Plugged in S-Video, now my video card is dead?"
date: 2006-07-26
forum: Multimedia &amp; Video
---

### Post by Maheriano on 2006-07-26
I have a dual head ATI Radeon video card which installed fine with Ubuntu, it had the same image on both screens. But today I rearranged my xorg.conf file to accomodate S-Video and rebooted using it just to make sure it works by itself. Then I plugged in the S-Video and rebooted and all 3 screens went crazy. When I removed the S-Video and rebooted, my screens didn't even come on, my system is complaining there's no devices found. But when I plug back into my onboard video, it works. I just can't get the monitors to come on with the video card anymore, I even reverted back to my previous working xorg.conf and still nothing.

---

### Post by Maheriano on 2006-07-26
I've spent the last 2 hours messing with it. I even reinstalled Ubuntu. Everytime I plug the VGA cable into the PCI video card, the monitor doesn't come on, even if I reboot. It will only work when plugged into the onboard video.

---

### Post by WaveMyBlackFlag on 2006-07-26
sounds like bios problem, not OS.  Try deactivating onboard video in your bios and set default display (if available) to PCI.

Only a thought

---

### Post by Maheriano on 2006-07-27
Never thought of that. However I've been at it for 11 hours now or about that. I pulled the video card from the computer completely and now everything is flawless. I wonder what'll happen once I put the video card back in......let's find out.

---

### Post by Maheriano on 2006-07-27
Wow, get this.
I just reinstalled Ubuntu without the PCI sound card and with the video card in a different (originally sound card) PCI slot. Everything was fine, the video card was in, however not in use, and it was all running fine. I shutdown, plug in the sound card, and bam....nothing. None of the monitors came on. So it's either the PCI slot the video card used to be in that's messed up, or it's been the sound card all along. Any ideas besides removing variables?

---

### Post by Maheriano on 2006-07-27
Shutdown, move monitor VGA cable from onboard to video card, reboot and again no monitors. Move VGA cable back to onboard, reboot, and it's fine again.

---

