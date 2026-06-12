---
title: "Wierd glitch with nvidia-glx-180 drivers"
date: 2009-03-13
forum: Multimedia Software
---

### Post by laserburn on 2009-03-13
I recently upgraded my video drivers from 177 to 180 using Synaptic (I'm guessing it probably got them from a multimedia repo that I added earlier). Everything went more-less fine with the exception of one annoying bug. 

When I login the picture is not properly centered, about half a cm of the picture on the right side of the screen is cut off and appears on the left side. Problem seemed to solve itself out when I changed the resolution scaling overlay setting in the nvidia driver manager utility (which should have no effect, since I'm using screen's native resolution), screen went black for a little and centered itself properly afterwards. But then I discovered that whenever I login again problem is back, so I just start a driver manager utility, screen turns off and centers straight. I temporarily solved the problem by adding Nvidia's utility to the list of apps that start when I login, but I'm looking for a more elegant solution. The login screen and everything that precedes it are centered as they should be. 

I'm using 64-bit Ubuntu 8.10 with 2.6.27-11 kernel and a GeForce Go 7600 graphics.

---

### Post by komputes on 2009-03-14
Doesn't the Nvidia X Server Settings allow you to save a static xorg.conf file. Try this:

1 - Press Alt-F2 and type in 
```
gksudo nvidia-settings
```

2 - Make the changes that fix the shift on your monitor

3 - In the option on the right named "X Server Display Configuration" click the button "Save to X configuration file" and save it to the default (/etc/X11/xorg.conf)

4 - Reboot. Is it magically delicious?

---

