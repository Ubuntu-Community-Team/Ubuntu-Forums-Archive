---
title: "S-Video Output on a Geforce4 Go 440 (Ubuntu 8.10 PPC on a Powerbook G4 17&quot;)"
date: 2008-12-11
forum: Multimedia Software
---

### Post by 0graham0 on 2008-12-11
Hi,

I am wondering if it is possible to get s-video output on a nvidia Geforce4 Go 440. I am running Ubuntu 8.10 PPC on a Powerbook G4 17".

I have read over some other posts which suggested editing the xorg.conf file. I have not tweaked the xorg.conf on this current install, and when I open the file /etc/X11/xorg.conf it is blank.

The video card shows up in lspci as:
```
0000:00:10.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
```

in lshw it shows up as:
```
 *-pci:0
          description: Host bridge
          product: UniNorth 2 AGP
          vendor: Apple Computer Inc.
          physical id: 100
          bus info: pci@0000:00:0b.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-uninorth latency=16 module=uninorth_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: NV17 [GeForce4 440 Go 64M]
             vendor: nVidia Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pm agp agp-2.0 bus_master cap_list
             configuration: latency=248 maxlatency=1 mingnt=5
```

Any help is greatly appreciated.

---

