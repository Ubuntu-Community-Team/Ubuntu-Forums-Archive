---
title: "no widescreen support for philips 241E1SB 24-inch"
date: 2011-08-06
forum: Multimedia Software
---

### Post by Siggij on 2011-08-06
Hi,
Just bought this monitor and it doesnt have widescreen support like my old Dell one but the crystal display in it is leaking across the screen. Maybe its just too new or something. I have little experience in configuring Xorg.conf although I'm pretty adept in other areas of Linux. Running ubuntu 11.04 gnome not unity or gnome-shell. The resolution is 1920x1080 (16:9), 60 Hz. with the default recommended nvidia driver. Can anybody please help? Maybe ran into the same situation or knows how to configure X. Would be very much appreciated. 

:mad:

---

### Post by realzippy on 2011-08-06
[http://ubuntuforums.org/showpost.php?p=11121095&postcount=2](http://ubuntuforums.org/showpost.php?p=11121095&postcount=2)
...feel free to ask

edit:
might also be something about:
HorizSync 30.0 - 83.0
VertRefresh 56.0 - 75.0

---

### Post by Siggij on 2011-08-06
Hi there, 
Did like you posted. Still doesnt work, your hsync and vrefresh rates were right. Found the manual online, cdrom doesnt work either. Attached the xorg.conf to this post. Maybe you can take a look at it and see if you find something wrong with it.

Best regards,
Siggi from Iceland.

---

### Post by realzippy on 2011-08-07
... xorg.conf is pretty messed up.
How many graphic cards and monitors do you use?
Please delete the current xorg.conf by:

```
sudo rm /etc/X11/xorg.conf
```
then create a new one:
```
sudo nvidia-xconfig
```
Then reboot.

Then create nvidia-bug-report by:
```
sudo nvidia-bug-report.sh
```

Post/attach the created file (it is in your user's home folder)

---

### Post by Siggij on 2011-08-07
Ok,
Did like you said. Here's the nvidia-bug-report attached.

---

### Post by Siggij on 2011-08-07
Forgot to answer your question. I have one graphics card, a Nvidia 8400 GS and then one on the motherboard but the Bios is configured to use the Nvidia one.

---

### Post by realzippy on 2011-08-07
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    FontPath        "unix/:7100"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

This is your current xorg.conf,since you have run "nvidia-xconfig" it is not messed up no more.But you have to edit again the valid Vrefresh/Hsync values and reboot or restart Xserver....then your desired resolution should work.

---

### Post by realzippy on 2011-08-22
Guess it worked...did it?
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

