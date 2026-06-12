---
title: "Fonts too Big"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by mikaelsnavy on 2008-03-02
Hello,
I have Kubuntu 7.10 and my fonts are HUGE! They take up a good portion of the screen an I can't do anything! I have a Radeon X800 and my computer is hooked up to a LCD tv. One word takes up like 1/5th of the screen! Since everything is SOOO BIG I cannot really do anything but boot into the terminal. I
Here are the relevant parts of my xorg.conf file. I have to type it out, so if anything else is needed, just ask. I do have LinuxMCE installed, so my xorg.conf file has a bunch of extra stuff from that.
```

Section "Device"
        Identifier     "ATI ..."
        Driver          "ati"
        BusID          "PCI:1:0:0"
        Option         "XvmcUsesTextures" "true"
        Option         "renderAccel" "true"
        Option         "NoDCCValue"
        Option         "UseEDID" "false"
        Option         "ExactModeTimingsDVI" "true"
        Option         "NoLogo" "true"
        Option         "NoBandWidthTest" "true"
        Option         "ModeValidation" "NoDFPNativeResolutio
nCheck, NoEdidMaxPC1kCheck, NoMaxPC1kCheck, AllowInterlacedModes, AllowNon60HzDFPModes"
        Option         "DynamicTwinView" "false"
        Option         "AllowGLXWithComposite" "true"
        Option         "AddARGBGLXVisuals" "true"
        Option         "ConnectedMonitor" "DFP"
EndSection

Section "Monitor"
     Identifier    "SANYO VIZON"
     DisplaySize  325 183
     Option         "DPMS" "false"
     Modeline      "1280x720"  74.250 1280 1390 1430 1650 720 725 730 750 +hsync +vsync
     HorizSync     20-500
     VertRefresh  59-61
EndSection 

Section "Screen"
    Identifier   "Default Screen"
    Device       "ATI ..."
    Monitor      "SANYO VIZON"
    DefaultDepth 24
   Subsection "Display"
        Modes   "1280x720"
        Virtual     1280 720
  EndSubSection
        Option         "XvmcUsesTextures" "true"
        Option         "renderAccel" "true"
        Option         "NoDCCValue"
        Option         "UseEDID" "false"
        Option         "ExactModeTimingsDVI" "true"
        Option         "NoLogo" "true"
        Option         "NoBandWidthTest" "true"
        Option         "ModeValidation" "NoDFPNativeResolutionCheck, NoEdidMaxPC1kCheck, NoMaxPC1kCheck, AllowInterlacedModes, AllowNon60HzDFPModes"
        Option         "DynamicTwinView" "false"
        Option         "AllowGLXWithComposite" "true"
        Option         "AddARGBGLXVisuals" "true"
        Option         "TVStandard"   "720p (16:9)"
EndSection
Section "Extensions"
          Option         "RENDER" "true"
EndSection

```
There may be some typo's because I by hand.
  Thanks,
  Mikael

---

### Post by mikaelsnavy on 2008-03-03
I reset my xorg.conf file and the problem is still there. I think it is in KDE.

---

