---
title: "A bagfull of Meerkat issues"
date: 2010-10-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by blueturtl on 2010-10-06
Installed the Ubuntu 10.10 RC yesterday.

Here are the issues I've encountered so far:

[LIST]
[*]Deluge will hang every time I try to quit it.
[*]Video playback in Totem is terribly laggy with the ATi open source driver. (Radeon HD 4650)
[*]Video playback in Totem is has VSYNC issues with the ATi Catalyst driver. (Radeon HD 4650)
[*]Adjusting the volume causes skips and weird artifacts in playback. (ASUS Xonar DX)
[*]Hidden toolbars won't appear unless I put the pointer in a corner (is this a bug?)
[*]Mantis DTV driver is apparently not working out-of-box (Terratec Cinergy-C HD)
[/LIST]

Known solutions to any of these?

---

### Post by glasen on 2010-10-06
> Deluge will hang every time I try to quit it.

This bug should be solved with the latest "libtorrent-rasterbar"-package update :

> libtorrent-rasterbar (0.15.4-0ubuntu1) maverick; urgency=low

  * New upstream bug fix release.
   - Fixed tracker announce issue which could cause high
     CPU and memory usage. (LP: #639659)
   - Fix issue which can cuase an infinite loop and result
     in Deluge lockingup. (LP: #654906)
   - Many thanks to Christophe Dumez, upstream author
     Arvid Norberg, and Daniel Hollocher for making
     sure these fixes landed in Maverick.

---

### Post by flammon on 2010-10-09
> **glasen said:**
> This bug should be solved with the latest "libtorrent-rasterbar"-package update :

Deluge still does not quit for me with the new package.

```

Architecture: amd64
Source: libtorrent-rasterbar
Version: 0.15.4-0ubuntu1

```

---

