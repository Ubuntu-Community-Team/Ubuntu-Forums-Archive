---
title: "Upgrade Broke NVIDIA Driver?"
date: 2011-02-16
forum: Mythbuntu
---

### Post by crbnrod on 2011-02-16
...I think. 

I updated/upgraded (through the update mgr) one of my mythbuntu boxes a few days ago, and after rebooting, I got a login prompt, which was new, and after logging in, I simply got a terminal prompt.

If I try to run nvidia-settings, I get an error message saying the control display is undefined.

I've tried using an old xorg.conf file as well as deleting the xorg.conf file and restarting to let it use default settings.
I've also tried 
```
sudo  dpkg-reconfigure xserver-xorg
```, has not helped.

The best I've been able to do is get to a graphical login screen. When I login to either mythbuntu or xfce, the computer does a little thinking and then sends me back to the login screen. 
I am able to login to an xterm session, but I can't run nvidia-settings from it (it just pulls up a dummy window with like four checkboxes) because it doesn't detect the x server as running..so then it wants me to run nvidia-xconfig and restart the x server and then I'm back to a terminal login when I restart.

Any ideas on what I can do or how I can further diagnose this? 
Graphics card is NVIDIA 6150 and the login is assuring me I've got 10.04 LTS.
Oddly enough, the backend (machine is FE/BE) seems to be loading fine and everything. 

Let me know if this is in the wrong place - wasn't sure if it belonged in the mythbuntu forum or somewhere else.

Thanks for any help.

---

### Post by nickrout on 2011-02-17
What version of the driver did you have before and what version now?

What does /var/log/Xorg.0.log say?

Is the nvidia driver loaded or are you presently running some fallback driver?

---

### Post by crbnrod on 2011-02-17
I'm pretty green at this stuff - how can I find out what driver I currently have (from command line)?

The xorg log says it failed to load the NVIDIA kernal module and to check the kernel log for add'l error messages.
it then unloads the nvidia module:
```
Unloading /usr/lib/xorg/extra-modules.nvidia_drv.so
v41 driver for Video4Linux
Primary Device is: PCI 00@00:05:0
Falling back to old probe method for v41
No devices detected.

Fatal server error:
No screens found
```

I don't think the nvidia driver loads at all no matter what I've done because even if I get a GUI I can't run nvidia-settings.

---

### Post by crbnrod on 2011-02-17
If sudo uname -r tells me what driver is installed, I have 2.6.32-28-generic.

---

