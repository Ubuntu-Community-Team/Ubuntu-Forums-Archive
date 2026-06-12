---
title: "screen resolution reset after reboot"
date: 2010-04-21
forum: Multimedia Software
---

### Post by jollyownes on 2010-04-21
Hi can anyone help?  My screen resolution keeps reverting back to the default resolution 800x600.  I'm using ubuntu 10.04, but had the same problem on 9.10 on my Acer Revo r3600 ION.  I am able to change the resolution to 1280x1024 but have to do it by the nVidia configuration tool.  The tool then allows me to 'Save to X Configuration' which it appears to have done successfully.  See the sections from my '\etc\x11\xorg.conf' file.  This is the state of the file after a reboot by the way.

Does anyone know how I can get my desired resolution to persist after I reboot?
  
Thanks, Ollie

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by JamesSmith on 2010-04-22
If I recall, when you change the resolution and click apply in the nVidia config tool, does it not give you a preview of the lines it's going to add to the xorg.conf file?

I remember having the same issue, where the resolution would be changed for the current session but would be reset after a reboot.  To fix it, I copied the preview of the nVidia xorg.conf and added the necessary lines into the system's xorg.conf file in /etc/X11/. You should then have lines for monitor name, gfx card name, screen res etc in the relevant sections.

I'm sorry I can't show you an example of the file because I'm at work atm and the computer I did this on belongs to my parents!

Hope that helps.

---

### Post by Grenage on 2010-04-22
I had the same problem on one machine, manually emptying the file worked for me:

```
#backup the old config:
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup

#create a new blank file:
sudo touch /etc/X11/xorg.conf

#Run Nvidia settings, make changes and save:
sudo nvidia-settings
```

---

### Post by selfcommander on 2012-04-25
For newest NVIDIA driver (271) this post [http://ubuntuforums.org/showpost.php?p=7490352&postcount=2](http://ubuntuforums.org/showpost.php?p=7490352&postcount=2) fixed it for me, saving or changing xorg.conf didn't work. Alternatively you can put xrandr -s 1920x1080 in startup script if above doesn't work

---

