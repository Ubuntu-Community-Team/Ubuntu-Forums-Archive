---
title: "Need help with my Xorg.conf file"
date: 2010-03-05
forum: Multimedia Software
---

### Post by Flaffen on 2010-03-05
I'm running UbuntuStudio 9.10 and I have Radeon 9200 pro (rev280) and I have installed the latest drivers (I am at least pretty sure). I tried following a manual on how to edit my Xorg.conf file, but when I restart I wind up having to choose low graphics mode because of some error.

My xorg.conf file looks like this:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "ati"
	BusID           "PCI:1:0:0"
        Option          "AccelMethod"   "EXA"
	Option          "TripleBuffer"   "true"
	Option          "BusType" "PCI"
        Option          "AGPMode" "1"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1440x900" "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection



I guess I messed it up somehow, what did I do wrong?

---

### Post by doas777 on 2010-03-05
under device try changing 
"Driver          "ati"" 
to ```
Driver "flgrx"
``` and reload x. see if that helps.

---

### Post by DasEi on 2010-03-05
with that 9200 you won't be happy using propitary ati drivers this time,as they are incompatible with current xorg-version. Best way to do this card now is using opensource radeon driver, which , though fglry works, too , is currently best solution.
You might be happier in lucid (ubu 10.04) , as there are some developments going on.

---

### Post by Flaffen on 2010-03-05
Well I cant use my fglrx driver, cuz it doesent support my card. But did I not mess anything up in the Xorg.conf file?

I should be able to use the ati or radeon drivers. But I thought my xorg.conf file messed things up.

---

