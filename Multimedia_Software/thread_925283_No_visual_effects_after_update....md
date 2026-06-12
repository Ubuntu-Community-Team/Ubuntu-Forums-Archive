---
title: "No visual effects after update..."
date: 2008-09-20
forum: Multimedia Software
---

### Post by tompug on 2008-09-20
..I have just updated from 7.10 to 8.04 and all the compiz effects no longer work. I still have access to 'advanced desktop effects' menu and compiz is still installed.

 I presume it's a graphics driver problem because upon reboot after the update, the restricted driver (previously disabled) insisted it needed to be activated and wouldn't quit until I did so. Another reboot and it's was running in low graphics mode (doh!). I then deactivated the restricted driver which returned my basic desktop settings (resolution,colours etc).

I'm a bit stumped, and being a relative newbie to linux, have no idea how to problem solve this. Any help much appreciated :)


Heres what xorg.conf says

```
 
     Identifier      "nVidia Corporation G71 [GeForce 7900 GS]"
        Driver          "nv"
        BusID           "PCI:5:0:0"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G71 [GeForce 7900 GS]"
        Monitor         "SyncMaster"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "80$
        EndSubSection
EndSection

```

---

### Post by overdrank on 2008-09-20
Hi and yes you are using the drive nv and the effects will not work unless you are using the nvidia driver. So you will need the restricted driver. What is the model of the graphics card?

Moved :)

---

### Post by tompug on 2008-09-21
Thanks for the reply, the card is an Nvidia 7900GS (Dell branded). Do I need to diable 'nv' driver and turn on the restricted driver?

---

