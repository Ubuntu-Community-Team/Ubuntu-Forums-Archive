---
title: "Warning about dropped support for ATI cards"
date: 2010-06-07
forum: Multimedia Software
---

### Post by boonenoob on 2010-06-07
[CENTER][SIZE=7]ATI Drivers and you:[/SIZE]

[SIZE=7][SIZE=4]how to avoid breaking your computer with drivers.[/SIZE][/SIZE]
[LEFT]
[CENTER][SIZE=4]Do _NOT_ update your drivers if you have these card(s)![/SIZE]

ATI Technologies Inc Radeon XPRESS 200M 5955 (Also Incompatible with(at least for me)Fgxlsti or w/e thats called)



[SIZE=5]
[/SIZE][SIZE=5]Q:How do I find out which card I have?[/SIZE]
[SIZE=5]A:Open up a terminal window and type:
[/SIZE][SIZE=4]```
lspci -v
```[/SIZE]
[SIZE=5]Look for:
[/SIZE]```
[SIZE=4]01:05.0 [/SIZE][SIZE=3][COLOR=Red]VGA compatible controller:[/COLOR][/SIZE][SIZE=3] ATI Technologies Inc [/SIZE][SIZE=3][COLOR=Red]Radeon XPRESS 200M[/COLOR][/SIZE][SIZE=3] 5955 (PCIE)
    Subsystem: Hewlett-Packard Company Device 30ae
    Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 17
    Memory at c8000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 9000 [/SIZE][SIZE=3]
    Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: radeon
    Kernel modules: radeonfb, radeon
[/SIZE]
```[SIZE=4]
[SIZE=5]Q: Oh snap! I already installed fgllrstx/ w/e thats called and now opengl wont work!! HEEEELP!
A:This will fix it:
[/SIZE][/SIZE]```
  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg

```[SIZE=4][SIZE=5] 
[/SIZE]I hope I've helped.[/SIZE]


Tell me some more unsupported cards and i'll add them.
[/CENTER]
[/LEFT]
[/CENTER]

---

