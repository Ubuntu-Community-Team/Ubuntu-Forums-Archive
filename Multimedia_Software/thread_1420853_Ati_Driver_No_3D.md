---
title: "Ati Driver No 3D"
date: 2010-03-03
forum: Multimedia Software
---

### Post by Soundpitchblack on 2010-03-03
Hey guys, first of all i'm new to linux systems installing linux I encountered a problem with my monitor being able to display I modified the x.org with "sudo nano /etc/X11/xorg.conf"
it shows the next:
Section "Device"
        Identifier      "Radeon 1600XT"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"

EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Radeon 1600XT"

        SubSection "Display"
                Modes         "1366x768" "1024x768" "800x600"

        EndSubSection

EndSection

Section "DRI"
        Mode 0666
EndSection
Section "Extensions"
        Option "Composite" "Enable"
EndSection

The Monitor now can display the resolution but I dont have 3D capbilities... 

If anyone can help it will be much appreciated !

---

### Post by Mark Phelps on 2010-03-05
If you mean you don't have 3D acceleration -- you will get very little of that, if any, using the open source driver.  

And, the ATI Linux drivers won't work with your card an any Ubuntu version newer than 8.10.

ATI dropped Linux support for your card long ago.

---

### Post by Yellow Pasque on 2010-03-05
Output of glxinfo?

> 3D acceleration -- you will get very little of that, if any, using the open source driver.
There should be enough 3D capability to run Compiz and some games (e.g. openarena). If not, something's wrong with the driver setup.

---

