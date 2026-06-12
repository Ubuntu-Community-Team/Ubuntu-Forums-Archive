---
title: "nVidia card not working on Lucid 64 bit"
date: 2010-04-28
forum: Multimedia Software
---

### Post by 5zerocool on 2010-04-28
I'm doing an install for a friend, the machine is a Gateway with AMD Turion64. The install required the 64 bit version of Lucid 10.04 RC. When I try to install the NVIDIA hardware driver, upon reboot, it flickers, fails, and tells me to use low-setting graphics mode.

lspci | grep VGA
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6100] (rev a2)

I have tried all 3 options in the Hardware Drivers menu with no success.
Any ideas?

---

### Post by limey_rick on 2010-04-28
I just did a quick check on the NVIDIA driver for your graphics card - see here: [http://www.nvidia.com/object/linux-display-amd64-195.36.24.html](http://www.nvidia.com/object/linux-display-amd64-195.36.24.html)

Looks like this is a version released today, so maybe if you try this, you may have some luck. I think it will download a script that you have to run in the shell, e.g.: 

> sudo sh *script.run*

If I ever had problems with NVIDIA graphics cards (not recently but I have in the past), I always went to get the latest drivers and these seemed to work out ok.

---

