---
title: "Ubuntu 7.04, GeForce 6200, and Samsung Plasma"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by serpicolugnut on 2007-08-10
I had been using my Ubuntu box with a Viewsonic LCD. I've now moved that box to my living room, and want to connect it to my Samsung Plasma. 

I've got the plasma connected to my video card (GeForce 6200 AGP), and Ubuntu loads fine. The problem is that I can't get any resolution on the display higher than 800x600.

The Plasma says it supports up to 1024 x 768 with the following frequencies:
60.004 vertical / 48.363 horizontal
70.069 vertical / 56.476 horizontal
72 vertical / 57.672 horizontal
75.029 vertical / 60.023 horizontal

How do I get Ubuntu to recognize these resolutions/frequencies?

Thanks!

---

### Post by Scunizi on 2007-08-11
You will probably need to edit the choices available in /etc/X11/xorg.conf

---

### Post by RomeReactor on 2007-08-11
Hi. If you've installed the **nvidia-glx** driver, try running **nvidia-settings** from the terminal:
```
gksudo nvidia-settings
```
then go to **X Server Display Configuration** (second option from the top, in the left pane) and see if you can increase the resolution there.

---

