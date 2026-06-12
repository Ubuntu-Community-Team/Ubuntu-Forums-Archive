---
title: "Screen resolution is super low and won't change"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by JoeyM on 2007-01-05
The screen resolution is stuck at 640x480, and when I try and select more from the drop down list, it's the only option. 
How do I get 1024x768 resolution?
Also, on the live cd it was 1024x768, no problem.

---

### Post by scrooge_74 on 2007-01-05
open a terminal window and do sudo dpkg-reconfigure xserver-xorg

You need to know the details of your monitor, vertical, horizontal sync, resolution capacity, your video card brand, so you can select one of the drivers there, if does not appear you may have to install them

---

### Post by JoeyM on 2007-01-05
> **scrooge_74 said:**
> open a terminal window and do sudo dpkg-reconfigure xserver-xorg

You need to know the details of your monitor, vertical, horizontal sync, resolution capacity, your video card brand, so you can select one of the drivers there, if does not appear you may have to install them

Alright, I'll try this and post again with how it went.

---

### Post by JoeyM on 2007-01-05
Awesome, it worked, thank you so much.

---

### Post by Five40 on 2007-01-06
> **scrooge_74 said:**
> open a terminal window and do sudo dpkg-reconfigure xserver-xorg

You need to know the details of your monitor, vertical, horizontal sync, resolution capacity, your video card brand, so you can select one of the drivers there, if does not appear you may have to install them
I'm having the same problem with my Nvidia 6600.

I've got the nvidia drivers installed, i've followed the instructions above restarted many times and the the resolutions I selected are still not available.

---

### Post by scrooge_74 on 2007-01-06
did you check the xorg.conf file in the driver section it should say nvidia instead of nv

---

