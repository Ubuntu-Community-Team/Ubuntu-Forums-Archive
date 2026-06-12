---
title: "dual monitors, two different video cards"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by stillspiraling on 2007-02-12
I know how to set everything up I'm fairly sure, but wanted confirmation on drivers and whatnot.

The first video card is on-board intel.  The second is an nvidia  in a pci slot.

I understand in xorg.conf I'll need to set up a device for each video card seperately, and specify the correct BusID in each one such as

```

Section "Device"
        Identifier      "Intel Corporation 82865G Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

```


Is this correct?  So for both cards it would look something like

```

Section "Device"
        Identifier      "Intel Corporation 82865G Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Device"
        Identifier      "Nvidia corporation example card"
        Driver          "nvidia"
        BusID           "PCI:1:1:0"
EndSection

```

And what about drivers?  Should I install nvidia-glx?  Should I use xinerama?  See how I specified i810 as the correct driver for the intel card but "nvidia" as the driver for the nvidia card - will this work?

The problem is that I don't have access to any video cards with dual output - just the onboard and an additional card I've plugged in.

THANKS in advance!


p.s. - Here's how my video cards read out in lspci

```

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
01:01.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

```

---

