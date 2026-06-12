---
title: "DVI-D to HDMI thinks my Samsung 42&quot; is only 7&quot;"
date: 2009-03-12
forum: Multimedia Software
---

### Post by ikunat33 on 2009-03-12
For some reason Ubuntu thinks my SAMSUNG 42" LCD is a SAMSUNG 7" LCD. I do not know why nor have I been able to find anything similar up to this point. 

Understandably my 42" LCD is a little insulted and refuses to co-operate. Trying different settings produces the same result in all cases:

"Mode Not Supported"

If anyone has any ideas on possible causes my system configuration and xorg.conf are shown below. If more information is needed I will supply it on request.

Thanks.


UBUNTU 8-10 + latest updates
Acer TravelMate 8204
ATI MOBILITY™ RADEON X1600
DVI-D

Using HDMI2/DVI as specified in SAMSUNG manual.

---------xorg.conf--------------
Section "Device"
        Identifier      "Configured Video Device"
        Option "AccelMethod" "EXA"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
--------------------------------

---

