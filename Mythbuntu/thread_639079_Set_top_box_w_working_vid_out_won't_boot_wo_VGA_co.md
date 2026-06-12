---
title: "Set top box w/ working vid out won't boot w/o VGA connection"
date: 2007-12-12
forum: Mythbuntu
---

### Post by thematadorme on 2007-12-12
I am trying to setup a set top box that connects to my TV through composite out. The video out works fine, but the system will not boot unless the VGA is also connected to a separate CRT monitor. I have used the BIOS to disable the VGA output completely. The only signal being sent is the video out. The CRT monitor does not need to be on. It doesn't even need to be plugged in! After boot up, I can disconnect the VGA cable and everything still works fin, but if I don't have the VGA cable connected at boot, all I get is this message:

"The display server has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again on display :0"

There must be a way to run Mythbuntu independent of a computer monitor! Any help would be appreciated.

System:
Motherboard/Processor: VIA VB7001 1.5GHZ
Hauppauge PVR 150
Dynex wireless G
Seagate 80GB
Morex 2766

---

### Post by thematadorme on 2007-12-16
So, after doing some research, I'm thinking that I need to disable "autodetect monitor" at startup. I've read that this can be accomplished by manually configuring xorg and telling it what monitor I have. Unfortunately, I have no idea how to do this! If someone could find it in their heart to walk me through this, it would really save Christmas. It doesn't even have to be my specific monitor, so long as it thinks it's a CRT. Even a max resolution of 800x600 would be fine.

---

### Post by mthaddon on 2007-12-19
What does your /etc/X11/xorg.conf look like?

Here's mine:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
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
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "DPI" "100x100"
    Option         "UseEvents" "1"
    Option         "AddARGBVisuals" "1"
    Option         "AddARGBGLXVisuals" "1"
    Option         "NoLogo" "1"
    Option         "UseDisplayDevice" "TV"
    Option         "TVOutFormat" "SVIDEO"
    Option         "TVStandard" "NTSC-M"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        # Modes      "nvidia-auto-select" "1920x1080" "1280x720" "1024x768" "720x480" "800x600" "640x480"
        Modes      "640x480"
    EndSubSection
EndSection
```

---

### Post by alus on 2008-02-14
I have the same problem described here, but it is occuring during install! I don't have a VGA monitor available to use - how can I work around this?

And, how can I file a bug so that this will be fixed?

---

### Post by drbisio on 2008-03-17
Hello,

a little question off-topic:  do you have 2d and mpeg acceleration working on this board? wich driver do yo use?


bye

---

