---
title: "xinerama on 8.04 not working for me"
date: 2008-08-20
forum: Multimedia Software
---

### Post by td3201 on 2008-08-20
Hello,

I have a very simple config that works if I disable xinerama but when I disable it, X just blows up.  I had bigscreen working under the ATI driver but I couldn't get a resolution better than 1024x768 so I am going down the open source route now.   I assume I have xinerama by this:

tdavis@tdavis-linux:~$ sudo aptitude search xinerama
p   libxcb-xinerama0                - X C Binding, xinerama extension           
p   libxcb-xinerama0-dbg            - X C Binding, xinerama extension, debugging
p   libxcb-xinerama0-dev            - X C Binding, xinerama extension, developme
p   libxinerama-dev                 - X11 Xinerama extension library (developmen
i   libxinerama1                    - X11 Xinerama extension library            
p   libxinerama1-dbg                - X11 Xinerama extension library (debug pack
p   x11proto-xinerama-dev           - X11 Xinerama extension wire protocol  


Here is my xorg.conf:

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "0 Configured Video Device"
        Driver          "ati"
        Option          "AccelMethod"   "EXA"
#       Option          "MonitorLayout" "TMDS,TMDS"
        Screen          0
EndSection

Section "Device"
        Identifier      "1 Configured Video Device"
        Driver          "ati"
        Option          "AccelMethod"   "EXA"
#       Option          "MonitorLayout" "TMDS,TMDS"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "0 Configured Monitor"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "1 Configured Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "0 Default Screen"
        Monitor         "0 Configured Monitor"
        Device          "0 Configured Video Device"
EndSection

Section "Screen"
        Identifier      "1 Default Screen"
        Monitor         "1 Configured Monitor"
        Device          "1 Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          0       "0 Default Screen"
        Screen          1       "1 Default Screen" RightOf "0 Default Screen"
#       Option          "Xinerama"
EndSection

---

### Post by td3201 on 2008-08-21
:( 

No ideas?

---

