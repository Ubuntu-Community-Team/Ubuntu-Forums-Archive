---
title: "ATI extended screen and problems with newly opened windows"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by mkljun on 2006-07-24
Hi!

I have extended my screen to the right the it is usualy extended in Windows XP. So My left part of the creen is on my monitor and the right part is on a TV. 

When I open a new application the windows always opens on the right side. So I can see it on a TV. I somehow understand it opens where are no other windows open but I it is a pain to move every new windows to the left.

Does anyone know how to force every windows to open on the left side of the screen? 

I have Ati Radeon 9200 and xorg.conf set up this way:

```
Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        # ########## disable PnP Monitor  ##########
        Option      "HWcursor" "yes"
        # ### generic DRI settings ###
        Option      "NoTV" "no"
        Option      "TVStandard" "COMPOSITE"
        Option      "TVHSizeAdj" "0"
        Option      "TVVSizeAdj" "0"
        Option      "TVHPosAdj" "0"
        Option      "TVVPosAdj" "0"
        Option      "TVHStartAdj" "0"
        Option      "TVColorAdj" "0"
        Option      "GammaCorrectionI" "0x06419064"
        Option      "GammaCorrectionII" "0x06419064"
        Option      "DesktopSetup" "0x00000200"
        Option      "MonitorLayout" "AUTO, AUTO"
        Option      "TVFormat" "PAL-G"
EndSection

```

---

### Post by Tristan9669 on 2006-07-31
yeah, I would like to know also

---

