---
title: "NVIDIA GeForce 7900 Driver Installation"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by NobleRooster on 2007-12-08
I am severly new to Ubuntu and I am trying to get the drivers for my NVIDIA GeForce 7900 and install them.

I have looked on here at different threads and scowered google for help but to no avail.  I also looked on the Envy website, but it is no help either.  Everytime I run Envy it says there is an error and won't install the drivers.

Is there any specific guide for the 7900 or can anyone point me to what I should be looking at/for with Envy?

---

### Post by NobleRooster on 2007-12-08
Please, I need some help here.

I have tried using Envy and everything els ebut nothing seems to work. HELP!

I got the driver installed now, or so I think...but on reboot, it did some sort of setup and now my screen resolution at it's highest is 800 x 600.

How can I reconfigure so that i can get a higher resolution?

---

### Post by sirdilznik on 2007-12-09
I've never used Envy personally.  I installed drivers for my 7950GT by enabling "Restriced Drivers" then installing nvidia-glx-new.  From the sound of it seems that the driver is installe but your /etc/X11/xorg.conf may be misconfigured which is why it X fails to start and it pops you into "Low Grahpics Mode'.  Have you tried running ```
nvidia-xconfig
```?

---

### Post by NobleRooster on 2007-12-09
> **sirdilznik said:**
> I've never used Envy personally.  I installed drivers for my 7950GT by enabling "Restriced Drivers" then installing nvidia-glx-new.  From the sound of it seems that the driver is installe but your /etc/X11/xorg.conf may be misconfigured which is why it X fails to start and it pops you into "Low Grahpics Mode'.  Have you tried running ```
nvidia-xconfig
```?

I haven't tried that yet, but I will next time I boot in Ubuntu.


Does anybody have any other suggestions?

---

