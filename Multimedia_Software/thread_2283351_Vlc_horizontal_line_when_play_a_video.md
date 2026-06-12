---
title: "Vlc horizontal line when play a video"
date: 2015-06-21
forum: Multimedia Software
---

### Post by anthony69 on 2015-06-21
Hi i try to play some video (.mkv) with Vlc 2.2.0. I have install vlc-plugin-libde265 but i when i play one video i see somethimes some horizontal line.. My system is Hp eny with i7 and Nvidia gtx 850m, and i have already install the driver nvidia.

How i can fix this problem?

---

### Post by monkeybrain20122 on 2015-06-21
This kind of artefacts seem to happen with Nvidia cards. Use a different Nvidia driver? There are many in the repo and you can get more updated ones from xorg-edgers.[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

You can also try disabling vdpau but that is kind of drastic.

---

### Post by anthony69 on 2015-06-21
> **monkeybrain20122 said:**
> This kind of artefacts seem to happen with Nvidia cards. Use a different Nvidia driver? There are many in the repo and you can get more updated ones from xorg-edgers.[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa)

You can also try disabling vdpau but that is kind of drastic.

Hi

i install nvidia driver 346.59.. but is possible vlc problem? or codec?

---

### Post by monkeybrain20122 on 2015-06-21
> **anthony69 said:**
> Hi

i install nvidia driver 346.59.. but is possible vlc problem? or codec?

Did you try mpv or Smplayer?

---

### Post by mc4man on 2015-06-21
> **anthony69 said:**
> Hi i try to play some video :  Nvidia gtx 850**m**, and i have already install the driver nvidia.

How i can fix this problem?
Mobile nvidia (optimus) will have tearing, (no vsync) on a compositing DE.
 (- if in fact you are using the nvidia drivers, provided by nvidia-prime & has to be specifically chosen in nvidia-settings.
 If using via nvidia-prime what happen in regards to the vid if you switch back to  the Intel gpu? 

I have a GT 755M here & never use it in Linux & never get any tearing ever with unity7 & compiz

---

