---
title: "how to fix Audio through HDMI Nvidia GTX 570 ?"
date: 2012-02-05
forum: Multimedia Software
---

### Post by hyperAura on 2012-02-05
I did a fresh install of Ubuntu 11.10 and I got a crystal clear image with HDMI hooked up without installing any extra drivers but no audio.

In System Settings-> Sound  under Hardware tab it says "GF110 High Definition Audio Controller", 1 Audio Output, Digital Stereo (HDMI) Output, so I am guessing the settings are correct.

The graphics card that I have installed is a Zotac GTX 570-Amp and I know that it works as I also have Windows installed and sound is working.

Please advice as what to do if you've had this problem as well

---

### Post by BicyclerBoy on 2012-02-05
You need to use the nVidia proprietary driver to have HDMI audio.
Your video card is a new model so you may need to get the driver from xorg-edgers ppa or similar.
Check the nVidia website for the required driver version but I do **not** recommend downloading the driver from there..

It is possible the nouveau driver project has some audio support.

You could check/post your /var/log/Xorg.0.log for the current video driver..

---

