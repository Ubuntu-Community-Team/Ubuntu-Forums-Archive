---
title: "nvidia question"
date: 2007-10-05
forum: Multimedia &amp; Video
---

### Post by scb0825 on 2007-10-05
Ok, so I know there are a thousand posts about nvidia drivers. I've spent quite sometime searching for an answer to my question, but have yet to find one. So here we go....

Recently I upgraded from an old MX 400 to a FX 5900 Ultra. Everything works fine after the upgrade... but the other day I was in xorg.conf and noticed that it still said I was using the MX 400. I searched around, found a few forums with suggestions. I used Synaptic and installed nvidia-glx-new (this process removed nvidia-glx). I then went to a prompt and ran "sudo nvidia-glx-config enable" like it said to in Synaptic. This said:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

So I ran "md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum", checked out xorg.conf to see if it made changes then rebooted. Thats when X took a **** and didn't load. I restored from a backup and everything is working as it was before the reboot. 

My question is this; does it matter if xorg.conf says I am using a MX400 if I am using an FX 5900? Will it cause any performance issues? I want to make sure I am using the proper driver for this card so that I can get the most out of it. Below is a copy of the xorg.conf. Thanks in advance for any help


Section "Device"
    Identifier     "nVidia Corporation NV11 [GeForce2 MX/MX 400]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV11 [GeForce2 MX/MX 400]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by nick_h on 2007-10-05
No that name is just an identifier - you can change it if you want.  The driver being used is the important thing.

If you have a look in /var/log/Xorg.0.log then you will see the chipset, memory etc... that is detected by the driver.

---

