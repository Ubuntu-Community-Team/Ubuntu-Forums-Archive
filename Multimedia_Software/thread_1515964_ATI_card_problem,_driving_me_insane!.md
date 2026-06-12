---
title: "ATI card problem, driving me insane!"
date: 2010-06-23
forum: Multimedia Software
---

### Post by carlsalter on 2010-06-23
Hi, 

I have two ATI PCIe cards in my machine that I use to drive four display panels.  They both worked perfectly on the same machine under XP and WIN 7.   I recently bit the bullet and moved to Ubuntu at work with a view of rolling it out to more machines in the office.  However, whereas my cards worked perfectly under 9.10, months of tinkering has not managed to get them both running under Lucid. 

Both are correctly identified with LSPCI...

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3600 Series
08:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3600 Series

but the Catalyst Control identities the non-default card as 'Unknown'.  Enabling the card anyway results in the Lucid being unable to boot.  I get the same effect using the built in ATI drivers.

Xorg.0.log reports nothing nothing interesting.  I've tried every version of the ATI driver that I can get my hands on.  Even a clean re-install resulted in exactly the same problem.

Rebooting back into Win 7 or 9.10 results in all four monitors bursting into life!

I nearly gave up yesterday and moved back to microsoft but thought I'd give it one last go...  

Can anyone throw some light on what might be the problem?

Cheers

Carl

---

### Post by carlsalter on 2010-06-23
It doesn't help that aticonfig --initial=dual-head --adapter=all -f makes an xorg.conf that appears to be about right! Both cards and all four monitors appear but it simply doesn't work!


Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[1]-1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1600x1200"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1600x1200"
    Option        "TargetRefresh" "60"
    Option        "Position" "1600 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "Default Device"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-1"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "0-DFP1"
    Option        "Monitor-DFP2" "0-DFP2"
    BusID       "PCI:8:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[1]-1"
    Driver      "fglrx"
    BusID       "PCI:8:0:0"
    Screen      1
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-1"
    Device     "aticonfig-Device[0]-1"
    Monitor    "aticonfig-Monitor[0]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]-0"
    Device     "aticonfig-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3200 3200
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[1]-1"
    Device     "aticonfig-Device[1]-1"
    Monitor    "aticonfig-Monitor[1]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

