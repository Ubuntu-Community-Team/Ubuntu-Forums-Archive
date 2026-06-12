---
title: "screen flickers"
date: 2008-04-27
forum: Multimedia Software
---

### Post by jeet on 2008-04-27
I have xubuntu Hardy Heron and this problem was there with previous install of Gursy also. The problem is that I frequently see flicker on screen. To be more precise I see and rapid switching of desktop switching between the four virtual desktops. Some times it stops by itself and other times I have to resort to ctrl-alt-backspace. I have Dell 1905fp LCD monitor and I have update horizSync and VerRefresh rate in xorg.conf. Here is relevant portion of my xorg.conf,
```

Section "Device"
        Identifier      "Trident Microsystems CyberBlade/i1"
        Driver          "trident"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       31-80
        VertRefresh     56-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Trident Microsystems CyberBlade/i1"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection


```

How can I fix this problem?

-Navjeet

---

