---
title: "fix for nvidia graphics card users stuck in 1024x768"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by xavierorr on 2007-11-09
When I installed ubuntu on a system with an nvidia card the system booted into 1024x768 resolution. when I went into the resolution options dialog the only options available were 1024x768 and lower even though my monitor supports up to 1600x1200 resolution. I had tried a number of different methods including the X configuration wizard but the following was the only thing that worked.

the following is an easy way to fix resolution for all nvidia users who have the nvidia driver installed.

1. open up terminal (Applications>Accessories>Terminal)

2. type in

sudo nvidia-settings

3. then press enter

4. on the nvidia control panel that comes up go into X Server Display Configuration

5. set the resolution you desire (typically 1280x1024)

6. then click Save to X Configuration File

7. close the window and restart your computer

---

### Post by satx on 2007-11-10
All,

Finally solved my problems w/Ubuntu 7.10 and my NVidia GeForce 7300 LE by installing Envy. After struggling with xorg.conf, correct NVidia driver selection, and using baseball bat to keep my graphics setting right, I downloaded this package. It automatically sensed the correct video card, installed all the right libraries, and correctly configured my card to provide 1280 x 1024 X 32 at 56Hz.

Go to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

SATX

---

