---
title: "nvidia/glx doesn't work after user logout"
date: 2009-05-01
forum: Multimedia Software
---

### Post by emkersyt on 2009-05-01
I have a problem logging out of my user. It doesn't come up again with the graphical interface after that. Normal boot works fine and there is no other trouble with the the nvidia driver so far.
I tried to fix it in failsafe mode and it gives me this error:

```
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(II) config/hal: Adding input device ThinkPad Extra Buttons
(EE) No input driver/identifier specified (ignoring)
(EE) config/hal: NewInputDeviceRequest failed

```
Apart from that there are no more errors in that logfile.
I am using GNOME on Ubuntu 2.6.27-11-generic (which was actually installed by the nvidia installer). My graphic card is  nVidia Corporation Quadro NVS 140M. My nvidia driver is version 180 (latest as far as I know). As I said the problem just occurs when I log out.


My xorg:
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
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection
```

Thanks for any help!

---

### Post by montini on 2009-09-26
Same here, Jaunty, Thinkpad R61, Nvidia Quadro NVS 140M, driver 185.18.14.

---

