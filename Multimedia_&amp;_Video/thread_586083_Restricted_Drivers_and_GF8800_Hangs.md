---
title: "Restricted Drivers and GF8800 Hangs"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by tbcpp on 2007-10-21
I installed Gusty, and it all went well. I have two 1620x1080 connected to a GeForce 8800 GTS via two DVI cables. With the nv driver they both work fine (mirrored) but only one shows up under the ubuntu graphics configuration utility. I installed the restricted drivers, rebooted, and got a screen saying my graphics configuration was incorrect (complete with the three retries with the screen flashing back to the text display). I set an acceptable mode, hit continue, and it hung with a black display. I even tried the nvidia driver direct from NVidia and nvidia-settings, and got pretty much the same results.

Any ideas?

---

### Post by ezak on 2007-10-21
Have you tried taking a look at your xorg.config file and checked to see if in the Section "Device" category, the Driver name has been changed to "nvidia" instead of "nv"?

---

### Post by tbcpp on 2007-10-22
Yeah, I even tried changing it once myself to nvidia. No use, it tells me that the configuration is bad.

---

