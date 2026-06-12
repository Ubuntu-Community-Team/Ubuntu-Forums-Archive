---
title: "Ubuntu 9.04 - Problems with display"
date: 2009-07-24
forum: Multimedia Software
---

### Post by andy_boy on 2009-07-24
Hi all, 

Just installed Ubuntu 9.04, and everything seems to be fine apart from an issue I'm having with the display. It seems to happen when there's two or more program windows open. Every now and then (around twice an hour), the program window will be filled with random garbage. Minimizing or changing the size of the window seems to fix it, but it's pretty annoying. Also, every now and then, mostly seems to occur when showing the desktop, a vertical line appears around 1/3 from the edge of the monitor, and the left and right parts are swapped over....

It is a Dell computer with a Dell 19" flatscreen monitor.  

Any ideas??

Please bear in mind that I'm new to Linux!

Thanks in advance.

---

### Post by xc3RnbFO8P on 2009-07-24
Open Terminal (Application> Accessories) and copy/paste into  window:
>  lspci | grep VGA
enter 
and show the output here

---

### Post by andy_boy on 2009-07-24
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

---

### Post by xc3RnbFO8P on 2009-07-24
Read this:
[http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

---

