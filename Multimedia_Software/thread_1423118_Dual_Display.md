---
title: "Dual Display"
date: 2010-03-06
forum: Multimedia Software
---

### Post by dsexton18 on 2010-03-06
Ok I have two monitors which I am trying to get working under Ubuntu 9.10. I installed the drivers and have got both dull monitors working. My hardware Nvidia 5200 and dull Dell 2001FP monitors It seams to see my second monitor right which is hooked up via dvi Monitor 1 also a Dell 2001FP is hooked up via VGA it seams to only think that it is also a VGA monitor and the resolution is so low it's a pain. How do I fix this so both display the same resolution. I had a how to that some what got me started but it didn't work. I can't seam to find it now. Any suggestions would be appreciated.

---

### Post by dsexton18 on 2010-03-07
I am trying to setup dull LCD monitors.  I have an nevidia 5200.  

Here are the steps I have taken install nvidia driver
Ran 
sudo nvidia-xconfig
then
**gksudo nvidia-settings**

but I always get failed while parsing file
I tried to delete the file  but get the same results

---

### Post by zeroseven0183 on 2010-03-07
When you go to System > Administration > Hardware Drivers, what do you see?

---

### Post by fermulator on 2010-03-07
First, you want to make sure you're running the latest nVidia proprietary (also known as binary) drivers direct from nVidia.

Example HowTo: [http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

Then, the easiest way to configure your monitors is using the nVidia control panel which will be installed automatically with the drivers.

[http://ravinsp.blogspot.com/2009/04/ubuntu-nvidia-control-panel.html](http://ravinsp.blogspot.com/2009/04/ubuntu-nvidia-control-panel.html)

The nVidia control panel has almost all the same and expected features as Windows.

TIP:  If you run the control panel as root, I believe the dual monitor settings will also be applied to Xserver, so that when you're at the login screen, dual monitor will also work there, instead of just for your user.

---

### Post by lyall on 2010-03-07
also see Configure_Dual_Monitors_with_nVidia
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Configure_Dual_Monitors_with_nVidia]("http://ubuntuguide.org/wiki/Ubuntu:Karmic#Configure_Dual_Monitors_with_nVidia")

good luck and have fun learning

---

### Post by overdrank on 2010-03-07
Hi and please do not create multiple threads on the same issue. Threads merged. :)

---

