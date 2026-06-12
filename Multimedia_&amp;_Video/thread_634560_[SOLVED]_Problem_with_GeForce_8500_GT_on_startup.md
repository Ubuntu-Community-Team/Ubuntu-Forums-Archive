---
title: "[SOLVED] Problem with GeForce 8500 GT on startup"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by snibbets on 2007-12-07
Hi,
I recently upgraded my system and now have a GeForce 8500 GT video card.  I have tried to use the nvidia-glx-new package, but was unable to get it to work for resolutions above 800 x 600.  So, I am now using the proprietary linux driver for the video card downloaded from nVidia's website.  This works just fine, except whenever I restart my system I am shown a dialog which says that my video card and monitor could not be detected.  I have to press Ctrl + Alt + Backspace and run the nVidia installer (NVIDIA-Linux-x86-100.14.19-pkg1.run) again (though when it says whether I want to install the driver again I click on No).  After this I start the GNOME display manager and everything works fine.  How can I avoid doing this every time I start my system?

Thanks
Simon

---

### Post by overdrank on 2007-12-09
> **snibbets said:**
> Hi,
I recently upgraded my system and now have a GeForce 8500 GT video card.  I have tried to use the nvidia-glx-new package, but was unable to get it to work for resolutions above 800 x 600.  So, I am now using the proprietary linux driver for the video card downloaded from nVidia's website.  This works just fine, except whenever I restart my system I am shown a dialog which says that my video card and monitor could not be detected.  I have to press Ctrl + Alt + Backspace and run the nVidia installer (NVIDIA-Linux-x86-100.14.19-pkg1.run) again (though when it says whether I want to install the driver again I click on No).  After this I start the GNOME display manager and everything works fine.  How can I avoid doing this every time I start my system?

Thanks
Simon

HI and welcome, I would suggest using Envy to install your drivers for the graphics card
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by snibbets on 2007-12-09
thanks.  worked like a charm.

---

