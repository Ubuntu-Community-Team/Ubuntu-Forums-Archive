---
title: "Newbie sound issue"
date: 2006-09-10
forum: Multimedia &amp; Video
---

### Post by techguyz8 on 2006-09-10
Hey, New user here to Ubunutu, I have a Asus motherboard with nvidia chipset and onboard sound. My sound works find on analog (plugged in with stereo 15mm plug) but when I try and use my fiber optic cable, I can't get it to work. I have ran aplay -l and lspci -v and my sound card has been installed correctly and is loaded. When I run alsamixer and setup my input to IEC958 and unmute the IEC958 channels my LCD readout on my speakers shows I am getting a signal but no sound. I had this working once before but had to reinstall Ubuntu as I broke something messing around :D Any help would be appreciated.

---

### Post by techguyz8 on 2006-09-11
Ok, now I have gone through and re-installed alsa acording to the sticky in this forum and have followed the steps for sound. I have a speaker icon in the top right of my gui, it doesn't have an x through it but I am still not gettting any sound. I have searched the forums and cannot find any threads on digital sound in ubuntu? Anyone know where there is a thread or guide for getting the digital (fiber optic IEC958) audio working? Thanks in advance.

---

### Post by techguyz8 on 2006-09-12
Ok. I was able to get my sound working but it isn't working like it was before. I had to switch over to the OSS driver rather than ALSA this time. Not sure why, but I was at least able to get sound. Anyone know if there is a disadvantage to using OSS over ALSA?

---

