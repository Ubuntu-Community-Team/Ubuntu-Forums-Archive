---
title: "Help getting ATI drivers to work"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by markcls on 2007-03-11
Hi,

I've been having trouble trying to get my ATI drivers. Seems like when I after booting up, there is no display on my screen.

This is my xorg.config file.

> 
Section "Device"
        Identifier  "ATI Radeon 9700"
        Driver      "ati"
        Option      "UseFBDev" "true"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx" 
        BusID       "PCI:1:0:0"

.....

Section "Screen"
        Identifier "aticonfig-Screen[0]"

        # I would comment either one out
        Device     "ATI Radeon 9700"
        #Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

EndSection

When I use "ATI Radeon 9700", I'm using the Mesa ATI drivers, right? Seems to work, but it's not the drivers that I would want, right?
When I try to use the fglrx drivers, I get no display. How do I get the fglrx drivers to work?

I'm super noob in linux, so please tell me what other information I should post, and how do I get the information...

Thanks :D

System Specs:
Pentium 4 2.4C HT
Abit IS-7
Powercolor ATI Radeon 9700
2*256 PC3200 Mushkin BlueLine DDR
120GB Maxtor Hard Drive
Sound Blaster Audigy DE

**EDIT: Problem solved. I had to add the Disable Composite extension as told on [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)**

---

