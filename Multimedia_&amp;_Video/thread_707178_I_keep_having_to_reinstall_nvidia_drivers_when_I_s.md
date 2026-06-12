---
title: "I keep having to reinstall nvidia drivers when I start my laptop"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by Persephone66 on 2008-02-25
Since I installed the Nvidia 169.09 drivers, every time I start my laptop I get a message telling me that ubuntu is running in low graphics mode. If I stop x, reinstall the Nvidia drivers, then restart x, everything is fine. Until I start the computer again. Any suggestions?

I'm running 7.10 on a Dell inspiron 1420 with an Nvidia Geforce 8400 .

---

### Post by Sam Lars on 2008-02-25
What does your xorg.conf say?

---

### Post by Persephone66 on 2008-02-25
> **Sam Lars said:**
> What does your xorg.conf say?

this is probly more than what you need.

```
Section "Device"
    Identifier     "Failsafe Device"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 8 Series"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"

 # 
    Identifier     "device1"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 8 Series"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M GS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Failsafe Device"
    Monitor        "Failsafe Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x960@60" "1280x1024@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
    EndSubSection
EndSection

Section "Screen"

 # 
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1024x768@60 +0+0; 800x600@60 +0+0; 640x480@60 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection
```

---

### Post by Sam Lars on 2008-02-25
Does that file change from when it goes to safe graphics to when you reinstall and it boots fine?
What's in your /var/log/Xorg.0.log (preferably after it goes to safe graphics)?

---

### Post by Persephone66 on 2008-02-27
> **Sam Lars said:**
> Does that file change from when it goes to safe graphics to when you reinstall and it boots fine?
stays the same
> What's in your /var/log/Xorg.0.log (preferably after it goes to safe graphics)?

There's a lot in there, what should I be looking for? I did notice that it said "Using config file "/etc/x11/xorg.conf.failsafe"" I also have a warning that dbe, dri, glx, and vbe will not be loaded.

---

### Post by Sam Lars on 2008-02-27
Try removing (or renaming) the xorg.conf.failsafe... I'm not sure why it tries to boot to that, or how it uses all the other xorg.conf.* files in there, but I've had success getting rid of them all to get it to boot to my regular xorg.conf.

---

### Post by Persephone66 on 2008-02-27
> **Sam Lars said:**
> Try removing (or renaming) the xorg.conf.failsafe... I'm not sure why it tries to boot to that, or how it uses all the other xorg.conf.* files in there, but I've had success getting rid of them all to get it to boot to my regular xorg.conf.

done, somehow it still went back to failsafe.

---

### Post by Sam Lars on 2008-02-27
So there's no xorg.conf.failsafe in /etc/X11, but the log still shows it booting to that file?

---

### Post by Persephone66 on 2008-02-27
it came back.

must have regenerated it

---

### Post by Sam Lars on 2008-02-27
Well then try copying the xorg.conf to xorg.conf.failsafe and see what you get.

---

### Post by Persephone66 on 2008-02-28
it's still forcing itself into low graphics mode. :(

---

### Post by Sam Lars on 2008-02-29
What does it say in the log?  Can you see if it's loading the settings you want but erroring for some reason?

---

### Post by forrestcupp on 2008-02-29
It seems like the drivers in the repos have that trouble.  I had to uninstall those drivers and use [Envy](http://albertomilone.com/nvidia_scripts1.html) to install the latest drivers from nvidia.  That did it for me.  I think the new drivers work better with the newer cards.

---

### Post by Persephone66 on 2008-03-04
I tried reinstalling with Envy.

still no luck

---

### Post by sanddgroper on 2008-03-04
Hi
What do.
dmesg
messages
syslog
Say in /var/log after you reboot

Cheers
Sandy

---

### Post by Persephone66 on 2008-03-06
I got it working.

I decided to do a fresh install, this time with kubuntu.

then, before I did anything else, I installed Envy and had it install the drivers.

Thanks everyone for your help. :)

---

