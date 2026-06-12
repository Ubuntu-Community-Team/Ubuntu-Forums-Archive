---
title: "[SOLVED] dual screen seperate screens (nvidia)"
date: 2008-01-22
forum: Multimedia &amp; Video
---

### Post by CheShA on 2008-01-22
Hi folks, thanks for reading, I hope youcan help.

I had a recent issue where the Ubuntu update installed an updated xserver-xorg and knackered my nvidia drivers. Anyway, long story short I installed an updated envy, removed and readded my nvidia kernel modules and then restored a backup of my old xorg.conf and everything is almost hunky dory.
Bizarrely, though, depite having exactly the same xorg.conf as I used to, my screen doesn't "work" quite like it did - I have one big screen instead of 2 seperate screens making a bigger screen.  i.e. before, windows would maximise to the current screen only; now they maximise to the entire desktop.  Confusingly, the GDM login screen still treats the two monitors seperately (i.e. login only appears on right screen instead of stretched across both as per Xinerama mode)

I am using Gutsy / Gnome / Nvidia 7600 / Envy 0.9.10 / Nvidia 169.07 / 2.6.22-14-rt

Also, nvidia-settings claims that I'm not using the nvidia driver and refuses to work.

Here is the xorg.conf, which, as I said, used to work as I wanted it to.

```

Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection
Section "ServerFlags"
    Option         "Xinerama" "0"
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
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "ButtonMapping" "1 2 3 6 7 4 5"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection
Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "BenQ FP91G+"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "BenQ FP91G+"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GS]"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7600 GS]"
    Monitor        "BenQ FP91G+"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
EndSection

Section "Screen"
   Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: 1280x1024 +0+0; CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

Has anyone seen this since the update? I'm pretty sure even that  I was using 169.07 drivers before too so the only thing that  has changed is the xserver-xorg.

---

### Post by scizzo on 2008-01-22
Xinerama is not very good working with nvidia cards at the moment

you should try to set it up with using the twinviews instead.

This you can do with the nvidia-settings when you have done a backup of the xorg.conf file.

---

### Post by scizzo on 2008-01-22
> **scizzo said:**
> Xinerama is not very good working with nvidia cards at the moment

you should try to set it up with using the twinviews instead.

This you can do with the nvidia-settings when you have done a backup of the xorg.conf file.

Ops noticed that you are using twinview.......sorry about that. Are you using xserver-xgl?

---

### Post by CheShA on 2008-01-22
Hi scizzo, thanks for the reply.

Yes that's what i don't understand... My desktop appears like xinerama but its set up for twinview in xorg.conf.  The Login screen appears as twinview.

How do I tell which xserver I'm using? I have a full compiz desktop.

Interestingly, while trying to find out, i ran a ps which shows this culprit running under my UID:
```
 Xgl :2 -accel xv:fbo -accel glx:pbuffer -nolisten tcp -fullscreen -br +xinerama
```

I'm not sure where that "+xinerama" is coming from?

---

### Post by CheShA on 2008-01-28
I created ~/.config/xserver-xgl/disable as per

[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/145182](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/145182)

---

