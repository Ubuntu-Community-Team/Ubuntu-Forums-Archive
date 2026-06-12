---
title: "recordmydesktop and maya issue"
date: 2008-06-09
forum: Multimedia Software
---

### Post by stealth_kid on 2008-06-09
hi. i have a small problem when trying to record the desktop using maya: the marking menus do not show in the video. for example, when i right-click on the channelbox, the menu that appears displays just fine in the maya window but is not seen in the video. i'm using ubuntu 8.04 64bit, recordmydesktop, maya 8.5 sp1 64bit. i attached two pictures with the settings for recordmydesktop. in xorg.conf the settings are as follows:
```

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
    Option         "NoLogo" "true"
    Option         "Coolbits" "1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024_75 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    Option         "DisableGLXRootClipping" "True"
    Option         "DamageEvents" "True"
    Option         "RenderAccel" "on"
    Option         "NvAGP" "1"
#    Option         "XAANoOffscreenPixmaps"
#    Option         "AllowGLXWithComposite" "On"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

```

in Maya.env i have set
```

MAYA_MMSET_DEFAULT_XCURSOR=1;
XLIB_SKIP_ARGB_VISUALS=1;

```

just in case it matters, i also use compiz. however, when i want to record the desktop, i disable it and set *Option "Composite" "Disable"* in xorg.conf. i did try with compiz enabled, but besides maya acting weird, those menus still don't show in the video.

does anyone know how to make the marking menus be captured properly by the screen recorder? thanks.

ps: if needed, i can post a small video sample.

---

