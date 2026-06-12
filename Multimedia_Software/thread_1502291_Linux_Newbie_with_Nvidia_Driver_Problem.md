---
title: "Linux Newbie with Nvidia Driver Problem"
date: 2010-06-05
forum: Multimedia Software
---

### Post by T_lewis_mitchell on 2010-06-05
I upgraded 9.10 to 10.04 and all seemed to be working properly, but I didn't like the desktop background. So I right-clicked on the background and opened display options where I saw three levels of graphic display. My system was set to lowest level entitled 'none.' Thinking 'none' should be improved, I clicked the middle level and Ubuntu aks me to install an nVidia 3d graphics driver. I clicked 'OK' and after the install was asked to reboot. Now Ubuntu dumps me to a tty login screen and it's command lines from there. Does anyone now how to get X and Gnome working again? My graphics card is nVidia GeForce 7500LE running on a HP PC.

---

### Post by rizzeh on 2010-06-05
to start/stop X:
```
sudo service gdm start  
sudo service gdm stop
```

---

### Post by T_lewis_mitchell on 2010-06-06
Thanks Rizzeh,

I used 'gdm start' and it appears that X is running but can't find a screen. I'm getting "fatal server error, 'No Screens Found'"

Is it possible to uninstall the driver and return the previous state? Or perhaps reinstall the previous drivers that 10.04 loaded with?

---

### Post by drdos2006 on 2010-06-06
The nvidia executable files I have in my machine are located in /usr/bin.
They are :
nvidia-uninstall, nvidia-xconfig, nvidia-settings, nvidia-installer and nvidia-smi. I would navigate to the /usr/bin directory and run ./nvidia-xconfig first. That might allow you set up /etc/X11/xorg.conf.....

regards

---

### Post by T_lewis_mitchell on 2010-06-06
Thanks drdos2006,
I'll give that try and let you know how it turns out.

---

### Post by T_lewis_mitchell on 2010-06-19
Well, the newbie has been on a rather steep learning curve. I'll skip the many dead ends I encountered. My problem was with X; the nvidia driver I installed failed to compile. From the Xorg.0.log file I discovered that nvidia module failed to load (did not exist) and that no other drivers were available. So I was getting the "Fatal Server Error: No Screens Found" message. Uninstalling the nvidia driver, reinstalling nouveau,and then reinstalling the nvidia driver from the command line and rebooting left me with X in low graphics mode. System > Administration > Hardware Drivers tells me that the nvidia driver is "active but not in use." At least I have basic GUI functionality and this newbie learned a lot about the command line. Thanks to those that helped. BTW, Nvidia's on-line documentation is superb. For others having Nvidia driver problems, check out:
[http://us.download.nvidia.com/XFree86/Linux-x86/195.36.31/README/](http://us.download.nvidia.com/XFree86/Linux-x86/195.36.31/README/)
Now I'm off to fix the remainder of my graphics problem.

---

