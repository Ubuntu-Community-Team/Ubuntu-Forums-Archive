---
title: "Desktop Effects not working using NVidia GO 7600, with 180.44 driver installed - 9.04"
date: 2009-08-05
forum: Multimedia Software
---

### Post by hermitt on 2009-08-05
Hey guys, so I'm running a Sony Vaio with a NVidia GO 7600 graphics card.  After a long and ardeous process, I was finally able to update to Jaunty and get the graphics driver installed (using NVidia's 180.44 driver).  However, when I click to enable desktop effects, it says "desktop effects could not be enabled".  I had them working a long time ago in gutsy, then re-installed everything, and now it doesn't work.  

The xorg.conf file is as follows 
```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

```





Under "hardware drivers", the 180.44 is checked and running fine.

Output of "nvidia-settings -q all |grep -i "driver" is :
```

NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
  Attribute 'NvidiaDriverVersion' (carson-laptop:0.0): 180.44 
```


Output of "compiz" is:
```
$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

```

, which then hangs, and when i finally cntl-C out of it, the window bars are missing, only to be put back to normal on a restart.


I think thats all that I can include.  The nvidia-bug-report.log is too big to upload here, but I can make that available should someone want it.

My end goal is to be able to run compiz with all of the fancy gadgets, widgets, whatnots and ballyhoo associated with it.  I have compiz installed, but without desktop effects being enabled, none of it works.  I have done a lot of searching throughout the weeks and have tried a lot of fixes, but none of them work.  If you can either help or point me in a direction I would be very grateful.

Thanks

Hermitt

---

