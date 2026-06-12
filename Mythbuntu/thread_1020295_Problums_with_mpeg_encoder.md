---
title: "Problums with mpeg encoder"
date: 2008-12-24
forum: Mythbuntu
---

### Post by realwildman on 2008-12-24
I just got done with installing mythbuntu 8.1.  Had been playing with xubuntu 7.1 with mythtv.  Was working good,  now is not.   After installing, my tuner is dropping frames and has digital artfacts in the video.  Some channels are worse than others.  Does it in vlc as well.  

Any ideas???

Hardware
asus a8m-vn csm
amd 3100 64bit single core
sata 300 harddrive
2 pvr-150's

---

### Post by ian dobson on 2008-12-24
Hi,

Maybe try adding afew buffers to the ivtv module with

echo "ivtv enc_mpg_buffers=9 ivtv_yuv_mode=2" >/etc/modprobe.d/ivtv.conf

It helped with the recoding on my PVR-500.

Also what resolution are you recording at? You should try recordng at the standard resolution of SD TV in your country.

Regards
Ian Dobson

---

### Post by realwildman on 2008-12-25
I try that its maybe alittle better but not munch.  
Also try what I hound here.
[http://ubuntuforums.org/showthread.php?t=713510](http://ubuntuforums.org/showthread.php?t=713510)

Still having trouble with it.

What I don't understand is why it was fine before I upgraded it but its not now.

---

