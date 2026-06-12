---
title: "X to failsafe after nvidia install"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by Namakemono456 on 2007-11-28
I tried posting on the NVidia forum about this but never got a replay..

Basically i do a freash install of Unbuntu, do the steps here: {[link]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")} and it works fine, until i restart my computer.
After the restart the screen goes to text based login, flashes 3 times, then enters safe graphics mode, i log in, and the x log says its using the failsafe config.
Any idea how to fix this?

---

### Post by Swooter on 2007-11-28
Try (from the terminal):

prompt> **sudo dpkg reconfigure xserver-xorg**

follow the prompted instructions to re-set up your Xserver.

---

### Post by Namakemono456 on 2007-11-28
what i tried today was to get it working with them installed with the nv driver, then enabling the nvidia driver, problem continued after i switched to the nvidia driver.

---

### Post by Yellow Pasque on 2007-11-29
post your /etc/X11/xorg.conf file

---

### Post by Namakemono456 on 2007-11-29
The nvidia created one or the one that i'm using now that the original modified as i set things up?

---

### Post by Namakemono456 on 2007-11-29
ill post a few here and their situation.

Open Source Driver and working is the first one (just conf)
Nvidia created one is the second one (conf.1)
And when i told the install to not auto update the xorg is the last one

---

### Post by Yellow Pasque on 2007-11-29
Give this one a shot:
```

Section "ServerLayout"
    Identifier     "Default Layout"
  screen 0 "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G71 [GeForce 7300 GS]"
    Driver         "nvidia"
    BusID	   "PCI:2:0:0"	
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7300 GS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by Namakemono456 on 2007-11-30
No such luck, worked until i restarted...i'm thinking it might be worth sticking with winblows until nvidia releases a final so unbuntu makes an official package....

---

### Post by Namakemono456 on 2007-12-01
I got it to work after installing nvidia-glx-new, but i cant seem to get the desktop effect to enable...what did i do now....

EDIT: forgot to mention NVIDIA X-server settings, runs fine so something must be right

EDIT2: i think i know whats wrong... the nvidia-glx-new version does not match the driver version....so what other package can i use that will work?

---

