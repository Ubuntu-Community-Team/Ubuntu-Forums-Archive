---
title: "Dual Monitor D630 Compiz problem"
date: 2009-05-13
forum: Multimedia Software
---

### Post by awreneau on 2009-05-13
I'm asking for the best of both worlds when I setup dual monitors and then enable Compiz but why not have your cake and eat it too?


I have compiz and dual monitors working w/o but with one caveat.

First let me define what my setup is.

Dell Latitude D630 w/ a LG L1718S monitor to the right of the laptop connected to the VGA output on the docking station.  I have dual monitors working w/ the folling in my xorg.conf file

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"

SubSection "Display"
Virtual 2560 1024
EndSubSection

The SubSection is the only modification I have made to the xorg file


Second mod I made was to skip checks on the compiz w/ the following 
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

After logging out and logging back in it worked with one exception.  On the right had side of the monitor, the screen will not refresh (screenshot attached). 

Not sure what the problem is, hoping someone might have some answers.

---

