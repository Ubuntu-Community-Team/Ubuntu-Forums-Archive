---
title: "Getting 1366x768 to work right on Feisty, nvidia 8500GT"
date: 2007-09-29
forum: Multimedia &amp; Video
---

### Post by emptymind on 2007-09-29
Hi

I am trying to run Feisty on AMD64 machine, with the NVidia 8500GT graphics card. My display is a 37" HP LCD with a "native" resolution of 1366x768 according to the manual.

As of now, I am not concerned with any 3D acceleration, just want to get it to work properly, so I haven't bothered with installing the latest nvidia drivers with Envy. 

I have tried several modelines in the Monitor section of xorg.conf and after a lot of trial and error, this one seems to come closest to working.

Modeline "1360x768@60" 72.05 1360 1408 1440 1520 768 771 776 790 -hsync -vsync

The trouble is that the only 2/3 of the picture is displayed on the screen (see attached image). I tried xvidtune and the TV settings to pan the image to the right, but this was the best I could manage. I tried several modeline generators on the web and gtf, but the one above was found on another forum. Any other modeline defaults to 1024x768 @ 60 which looks downright ugly.

Another thing I tried was to install Win XP 64 bit and download the latest nvidia drivers and conf tools. It is possible to enter a custom resolution through the nvidia control center on Windows but after setting 1366x768, the picture looks exactly the same as it does on Ubuntu - i.e. only 2/3 of the screen is visible. 

Any help will be greatly appreciated.:confused:

---

### Post by emptymind on 2007-09-30
anyone??

---

