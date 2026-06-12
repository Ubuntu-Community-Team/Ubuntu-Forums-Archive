---
title: "Rotation of screen with xorg.conf for Ivy Bridge (Failure for HDMI connector)"
date: 2013-09-13
forum: Multimedia Software
---

### Post by ODBWilson on 2013-09-13
OS: Mythbuntu 12.04
Kernel: 3.2.0-29-generic-pa
Driver: xserver-xorg-video-intel          2:2.17.0-1ubuntu4.4
vaapi: libva-intel-vaapi-driver             1.0.15-1ubuntu2

I am able to rotate the screen right with xorg.conf for VGA connector, but it was failed when using HDMI connector.

Here is the xorg.conf
=============
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        Option       "Rotate" "right"
EndSection

/var/log/Xorg.0.conf (HDMI connection)
==========================
[     5.087] (II) intel(0): **Output VGA1 using monitor section Monitor0 (Wrong Detection!!!)**
[     5.087] (**) intel(0): **Option "Rotate" "right"**
[     5.095] (II) intel(0): Output HDMI1 has no monitor section
[     5.140] (II) intel(0): Output DP1 has no monitor section
[     5.392] (II) intel(0): **Output HDMI2 has no monitor section (Why not detected?)**
[     5.396] (II) intel(0): Output HDMI3 has no monitor section
[     5.444] (II) intel(0): Output DP2 has no monitor section
[     5.492] (II) intel(0): Output DP3 has no monitor section
[     5.498] (II) intel(0): EDID for output VGA1
[     5.502] (II) intel(0): EDID for output HDMI1
[     5.548] (II) intel(0): EDID for output DP1
[     5.804] (II) intel(0): **EDID for output HDMI2**
[     5.804] (II) intel(0): Manufacturer: GSM  Model: 5872  Serial#: 16843009
[     5.804] (II) intel(0): Year: 2010  Week: 1
[     5.804] (II) intel(0): EDID Version: 1.3
[     5.804] (II) intel(0): Digital Display Input
[     5.804] (II) intel(0): Max Image Size [cm]: horiz.: 51  vert.: 29
[     5.804] (II) intel(0): Gamma: 2.20
[     5.804] (II) intel(0): DPMS capabilities: StandBy Suspend Off

....
....
....
[     5.810] (II) intel(0): **Printing probed modes for output HDMI2**
[     5.810] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[     5.811] (II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
....
....
[     5.980] (II) intel(0): EDID for output HDMI3
[     6.028] (II) intel(0): EDID for output DP2
[     6.272] (II) intel(0): EDID for output DP3
[     6.272] (II) intel(0): Output VGA1 disconnected
[     6.272] (II) intel(0): Output HDMI1 disconnected
[     6.272] (II) intel(0): Output DP1 disconnected
[     6.272] (II) intel(0):** Output HDMI2 connected**
[     6.272] (II) intel(0): Output HDMI3 disconnected
[     6.272] (II) intel(0): Output DP2 disconnected
[     6.272] (II) intel(0): Output DP3 disconnected
[     6.272] (II) intel(0): Using user preference for initial modes
[     6.272] (II) intel(0): **Output HDMI2 using initial mode 1920x1080**

Why is it always detected VGA1 as connector for Monitor0 even if I connect HDMI connectior?
And afterward, it can fetch the EDID for HDMI.
And I think it's the reason that the screen can't rotate right as expected when using HDMI.

P.S.  It works perfectly for VGA connector.

Any clues?

Thanks,
Wilson

---

### Post by ODBWilson on 2013-09-16
Any clues?

---

### Post by arronwall1 on 2013-10-30
[COLOR=#000000]Hi, I am almost a green hand on the related [/COLOR][[COLOR=#000000]image manipulating[/COLOR]]("http://www.yiigo.com/guides/vbnet/")[COLOR=#000000] program. But have you ever tried to deal with it using some [/COLOR][[COLOR=#000000]image rotators[/COLOR]]("http://www.yiigo.com/guides/csharp/how-to-rotate-image.shtml")[COLOR=#000000]? You can google it and select manual one which can be customized byusers according to your own favors. Remember to check its free trial package first if possible. I hope you success. Good luck.



Best regards,
Arron[/COLOR]

---

