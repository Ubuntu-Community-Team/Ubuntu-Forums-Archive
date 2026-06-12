---
title: "Wrong resolution on external monitor, laptop."
date: 2005-11-15
forum: Multimedia &amp; Video
---

### Post by damberg on 2005-11-15
I've been trying for days to get my hdtv running at 1368x768 but I can only get 1024x768. I've run the fglrxconfig  and set up as dualmonitor and it works. But the resolution is too low. I've modified my xorg.conf adding hertz and calculated my own modeline but still its only shows 1024x768. My laptop lcd works fine at 1400x1050. Help plz.

---------
Section "Monitor"
    Identifier  "Monitor1"
    HorizSync 30-61
    VertRefresh 60-75
    Option "DPMS"
    DisplaySize 603 342
    Modeline "1360x768" 84.50 1360 1392 1712 1744 768 783 791 807 +HSync +VSync

EndSection

Section "Screen"
    Identifier  "Screen1"
    Device      "ATI Graphics Adapter connector 1"
    Monitor     "Monitor1"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1360x768"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

Edit: Xorg.0.log:
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Dual head is configured, DesktopSetup setting "(null)" will not be used

I had no messages about EDID but I tried anyway to use the Option "IgnoreEDID" "True", only resulting in:
(WW) fglrx(0): Option "IgnoreEDID" is not used

No EE messages.

---

