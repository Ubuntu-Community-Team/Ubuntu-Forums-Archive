---
title: "Why install fglrx?"
date: 2005-10-17
forum: Multimedia &amp; Video
---

### Post by M4l3k on 2005-10-17
Hi all,

I am wondering why the default ati drivers are not good enough?
Personnaly, I want to make my dual monitor system work and am not convinced that fglrx is the way. Isn't that a matter of writing some extra lines in /etc/X11/xorg.conf?

Could some of you give me some input to help understanding this?

Thanks

M4l3k

---

### Post by KingBahamut on 2005-10-17
The Default ones , if you have a radeon card, do not accelerate near to the level that ati's drivers do. 

I would be "easier" to let fglrx handle your dual monitor setup, though installing the driver can be a little tedious at times.

---

### Post by M4l3k on 2005-10-17
[QUOTE=KingBahamut]The Default ones , if you have a radeon card, do not accelerate near to the level that ati's drivers do. 

I would be "easier" to let fglrx handle your dual monitor setup, though installing the driver can be a little tedious at times.[/QUOTE]

Do you then mean that it is possible to configure dual monitor with the default drivers? If yes, should I just edit the xorg.conf file and add the required info? 
Having in mind that I am not willing to use the 3d possibilities (if any!) of my graphic card, do you think it would make a difference performance-wise?

Thanks

M4l3k

---

### Post by KingBahamut on 2005-10-17
Youll need to make it look similar to this 

> ...
Section "Device"
    Identifier "device0"
    VendorName "ATI"
    BoardName "ATI Radeon"
    Driver "radeon"
    BusID "PCI:1:0:0"
    Option "DDCMode" "on"
    Option "DPMS"
    Screen 0    
EndSection

Section "Device"
    Identifier "device1"
    BoardName "ATI Radeon"    
    Driver "radeon"
    BusID "PCI:1:0:0"
    Option "DDCMode" "on"
    Option "DPMS"
    Screen 1        
EndSection

Section "Monitor"
    Identifier "monitor0"
    Option "dpms"
EndSection

Section "Monitor"
    Identifier "monitor1"
    Option "dpms"    
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "device0"
    Monitor "monitor0"
    DefaultColorDepth 24
    Subsection "Display"
        Depth 24
        Virtual 1280 1024    
        Modes    "1280x1024" 
    EndSubsection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 24
    Subsection "Display"
        Depth 24
        Virtual 1280 1024    
        Modes    "1280x1024" 
    EndSubsection    
EndSection

Section "ServerLayout"
    Identifier "Multihead layout"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "Mouse0" "CorePointer"
    Screen  "Screen0" 0 0
    Screen  "Screen1" RightOf "Screen0" 
EndSection

---

