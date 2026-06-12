---
title: "No Sound After Installing Pinnacle PCTV 800i"
date: 2008-08-24
forum: Multimedia Software
---

### Post by Number1Dad on 2008-08-24
I bought a Pinnacle PCTV 800i for my Dell Dimension 2400 running Mythbuntu 8.04. I extracted the tuner firmware and made the drivers as instructed here:

[http://www.mythtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29](http://www.mythtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29)

I didn't get sound. So, I followed what was suggested in the bottom paragraph and installed an Intrepid 2.6.25 kernel and removed the old kernel. I still didn't get sound, even after reinstalling the firmware and drivers. I then tried testing the sound in a video file that I knew worked. No sound. I tried all three /dev/dsp settings in the backend setup. Suggestions? My sound card is the integrated one that came with the Dimension 2400, I can get more info on it when I get home.

---

### Post by Number1Dad on 2008-08-25
After some investigation, I've found that my PC Speaker was the default ALSA device. Now the intel integrated is my default device, all of my sliders on the mixer are up, and I'm still getting no sound. I tried to introduce a fresh driver, but I guess since ALSA isn't built into this kernel, the modprobe didn't work. I'm not very good with Linux, but I'm assuming this is a missing driver.

---

### Post by Marsupilami23 on 2008-08-27
It does work, go here for more info. 

[http://ubuntuforums.org/showthread.php?t=602039&highlight=800i](http://ubuntuforums.org/showthread.php?t=602039&highlight=800i)

Page 6, half way down there is the answer. You will have to download the newest kernel, enable ALSA in the kernel as modules, compile  the kernel then compile v4l.

If you have any problems, let me know. Oh... and I would definately make sure you know what module your wireless networking uses. If it's in the kernel, make sure you mark it as a modules. Just in case, download everything first before starting on your new adventure. :)

---

