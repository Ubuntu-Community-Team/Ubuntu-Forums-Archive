---
title: "2nd video card recognized"
date: 2006-12-27
forum: Multimedia &amp; Video
---

### Post by josh76 on 2006-12-27
I am trying to get two monitors set up.  I have two identical video cards ().  One of them is not being recognized.

When I do a lspci -v, I am getting: 
[COLOR="Blue"]0000:00:0a.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] (prog-if 00 [VGA])
        Subsystem: PC Partner Limited: Unknown device 7c02
        Flags: bus master, stepping, medium devsel, latency 32, IRQ 177
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at d000 [size=256]
        Memory at e2020000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:00:0b.0 5159: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] (rev 02) (prog-if 10)
        !!! Unknown header type 10[/COLOR]

I would like to:
1. Have Ubuntu recognize the second card ?

2. Find out what the BusID is ?

Please help.

---

### Post by deadgobby on 2006-12-27
Here is some thing I found in Ubie's wiki
[https://help.ubuntu.com/community/XineramaHowTo](https://help.ubuntu.com/community/XineramaHowTo)

---

### Post by majoridiot on 2006-12-27
make sure you have a second device section in your /etc/X11/xorg.conf for that card and
use int10module to boot it up so x recognizes it.  use the lscpi info to fill in the busID-

```
Section "Device"
   Identifier "PCI"
    Driver      "<your ati driver>
    BusID       "PCI:0:10:0"
    Option      "UseInt10Module" "1"
    etc...
EndSection
```

that should get it working in X and you can work on xinerama, etc.

---

