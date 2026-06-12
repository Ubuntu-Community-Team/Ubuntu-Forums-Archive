---
title: "ALC880 audio chipset on ABIT AA8 motherboard"
date: 2005-10-26
forum: Multimedia &amp; Video
---

### Post by xmas_beetle on 2005-10-26
Hey guys

I switched over to Breezy about a week ago but could'nt get it to boot. It kept getting stuck while trying to load hotplug. I was stump for a while. Eventually I disabled all my onboard devices and reliased that the onboard sound was the problem. So now I'm sitting with no sound.:( 

Does anybody know if there is an issue with the ALC880 chipset?? 

Thanks

---

### Post by xmas_beetle on 2005-10-26
Got it working. It turned out to be quite simple.

Had the device disabled in the bios and booted up. Added snd_hda_intel to the hotplug blacklist. Rebooted enabled the onboard audio in the bios. Once it had rebooted I removed the module from the blacklist. Downloaded the latest ALSA drivers. Installed them and hey presto!! It works!!

---

