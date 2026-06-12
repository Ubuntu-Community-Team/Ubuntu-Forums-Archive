---
title: "problem with second display"
date: 2009-08-21
forum: Multimedia Software
---

### Post by el_kolo on 2009-08-21
hi,

i have problem with my ibm surepos 545 system. I pluged-in an additional display (also ibm) and it doesn't wake up (NO VIDEO - info on the screen). How to fix this? Ubuntu is after reinstalation.
Some system info: 
```

ibm@ibmpos:~/Pulpit$ lshw -C display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82915G/GV/910GL Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Radeon RV100 QY [Radeon 7000/VE]
       vendor: ATI Technologies Inc
       physical id: c
       bus info: pci@0000:01:0c.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=8 mingnt=8

```

xorg.conf (few days ago everything was ok with the same settings in this file - till I messed up and had to reinstall OS)
```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

---

