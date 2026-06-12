---
title: "Gutsy - Second monitor will not turn on with Radeon driver"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by jrj127 on 2007-11-24
I have a dual-head CRT-display setup that worked with Feisty.  It consists of an ATI Radeon 9600 (RV350), a Compaq P1100, and a Compaq V1100 (both CRT monitors).

When my computer boots, both the kdm and KDE desktop only activates the VGA-0 output (Compaq P1100 CRT monitor-Left).  When I execute these commands, the desktop grows correctly but the DVI-0 output does not turn on the Compaq V1100 CRT monitor-Right:

Attached is my xorg.conf file.  These are the versions included with Gutsy:
```
xrandr-1.2
xorg-7.2
xserver-xorg-7.2
xserver-xorg-core-1.3
xserver-xorg-video-ati-6.7.195
```

```
xrandr --addmode DVI-0 1600x1200
xrandr --output DVI-0 --mode 1600x1200 --right-of VGA-0
```
Is the problem:
[LIST=1]
[*]Do I need xorg-7.3 and xserver-xorg-core-1.4?
[*]Is the monitor too old to be detected (~1999)?
[*]The DVI->VGA adapter I use?
[*]Do I need to add a Device Section in xorg.conf for the PCI:1:0:1 secondary adapter?
[*]Is there a bug in the radeon driver?
[/LIST]

---

### Post by jrj127 on 2007-11-27
bump

---

