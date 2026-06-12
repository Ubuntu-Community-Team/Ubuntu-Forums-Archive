---
title: "xorg.conf weird after xserver update, bad?"
date: 2006-08-24
forum: Multimedia &amp; Video
---

### Post by whatrucrazy on 2006-08-24
[I][Originally Posted by Craftaz
yeah.. after installing drivers my gf Ti 4200 became a ATI RV100 DDD is it a joke or what???
-----------------------------before----------------------------
Section "Device"
Identifier "NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
Driver "nv"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 30-100
VertRefresh 60-160
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"

------------------------------------after-----------------------
Section "Device"
Identifier "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
Driver "nvidia"
BusID "PCI:0:5:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
Monitor "Generic Monitor"
----------------------------------------------------
did I do something wrong?...]
[/I]

hmmm, me too, seems like the xserver update issue is more than just going to 10.4:

i just checked my xorg.conf and have found the same thing. my graphics card is an nvidia Gforce4 MX420, yet now the config file says:

Section "Device"
Identifier "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
Driver "nvidia"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
Monitor "Generic Monitor"

i have updated to 10.4, and used the envy script to update my nvidia driver.

what's going on then? is this an issue that should be fixed? how?
a few people have asked this now but no-one has answered yet.:confused:

---

