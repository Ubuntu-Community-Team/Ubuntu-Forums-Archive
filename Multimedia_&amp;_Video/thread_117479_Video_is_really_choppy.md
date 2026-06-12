---
title: "Video is really choppy"
date: 2006-01-15
forum: Multimedia &amp; Video
---

### Post by mikerobinson on 2006-01-15
For normal desktop usage, everything seems to be perfectly fine, but when I try to run anything with openGL or play video files (avi, mpg, wma, etc) it is REALLY choppy. I remember playing tuxracer on this computer before and getting 40+ fps, now I get about 0.2 fps. My video card was recognized, even the correct model, but I'm not sure if openGL is working or not. Maybe it's some other problem.

# glxinfo|head -4
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI

# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

I have an ATI Radeon 32 meg (7000). I have the driver that was installed automatically when installing ubuntu.

---

### Post by Mr_Grieves on 2006-01-15
Try installing ATIs own driver.

```

sudo apt-get install fglrx-driver

```

Here's som ATI links for you aswell.

ATIs Linux driver: [http://www.ati.com/support/driver.html](http://www.ati.com/support/driver.html) 
Official ATI+Linux Howto: [http://www.rage3d.com/content/articles/atilinuxhowto/](http://www.rage3d.com/content/articles/atilinuxhowto/) 
Official ATI+Linux FAQ: [http://www.ati.com/products/catalyst/linux.html](http://www.ati.com/products/catalyst/linux.html) 
Official ATI+Linux forum: [http://www.rage3d.com/board/forumdisplay.php?f=61](http://www.rage3d.com/board/forumdisplay.php?f=61)

---

