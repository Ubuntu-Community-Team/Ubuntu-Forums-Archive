---
title: "VDPAU black screen"
date: 2010-04-05
forum: Mythbuntu
---

### Post by bnhrobotics on 2010-04-05
I have [_this_]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814133245") GeForce 8400 graphics card and an HVR-1600. My computer is slow so I wanted to add VDPAU support. So I changed the settings and tried both VDPAU Normal and VDPAU slim in the front end configuration setup. Now when I try to view live tv or watch a recording I get a black screen that never goes away. My computer becomes completely unresponsive and I end up with a black screen until I hold the power button. Any ideas? Thanks

---

### Post by singedwings on 2010-04-05
Did you upgrade to the fixes builds of mythbuntu? If not I would recommend it to get vdpau working. [http://mythbuntu.org/auto-builds]("http://mythbuntu.org/auto-builds")

Also use the nvidia vdpau ppa for the same reason available at [https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/~nvidia-vdpau/+archive/ppa")

This post will help you get vdpau with other programs as well [http://ubuntuforums.org/showthread.php?t=1037625&highlight=vdpau]("http://ubuntuforums.org/showthread.php?t=1037625&highlight=vdpau")

---

### Post by zorro07 on 2010-04-07
hi did you recently upgrade the nvidia driver to the 195 driver or similar?  if so you will need to run the xconfiguration utility to set up the xserver properly.  I had the symptoms u mention until i ran the config tool.  google for the details cant remember the exact command right now,  let us know how u get on..

cheers

---

### Post by bnhrobotics on 2010-04-11
Thanks. Seems that I have gotten that taken care of. Now I just need to figure out how to get the image to fit my screen. With VDPAU mythtv seems to be shrinking the video feed down on my monitor and padding it with black screen. Any idea what to do about that? Thanks

---

