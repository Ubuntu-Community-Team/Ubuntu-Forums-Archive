---
title: "Nvidia driver problems"
date: 2008-08-19
forum: Multimedia Software
---

### Post by chkneater on 2008-08-19
I have an Nvidia TNT2 card with 8mb of onboard ram.  When I first installed Ubuntu 8.04, the card seemed to work fine, but no Nvidia splash at startup and FlightGear ran none at all.  After much research, I decided I needed to try and reinstall the glx-legacy .dev and kernel.  This helped none.  I then found EnvyNG, which installed the same drivers I already had, but somehow it boosted the framerate significantly and I also got the Nvidia splash at startup.  However, the framerate varies dramatically allowing FlightGear to run superbly sometimes (now I know it is possible!), but slows down soon after startup and runs at a subpar rate.  I also cannot access nvidia-settings. I get this whenever I try to access X server settings:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.  

It tells me to run nvidia-xconfig as root, which when I do I get this:

The program 'nvidia-xconfig' can be found in the following packages:
 * nvidia-xconfig
 * nvidia-glx
 * nvidia-glx-new
Try: sudo apt-get install <selected package>
bash: nvidia-xconfig: command not found

Now, when I download and install nvidia-xconfig it uninstalls nvidiaglx-legacy .dev and kernel and on rebooting, the graphics resort to low graphics mode and I have to use envyng again to get the graphics back to normal.  I know this card is not a powerhouse, but it has run FlightGear VERY well at certain points, but not all the time. I have a 900Mhz processor and 640mb of RAM  I just know it has got to be something to do with the drivers.  Any tips on getting this to run better?

---

### Post by tuxxy on 2008-08-19
Have you tried nvidia-settings. 

```
sudo apt-get install nvidia-settings
```

---

### Post by chkneater on 2008-08-19
When I tried the nvidia-settings install, it tells me I have the newest version and it doesn't remove or install anything.  When I try to run nvidia-settings I get the same result as trying to run the X server settings, which is:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

And then of course, running nvidia-xconfig uninstalls the drivers and ruins my setup, which I have to use envyNG to fix it.

---

