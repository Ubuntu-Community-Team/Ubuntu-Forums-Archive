---
title: "Glitches in 3D rendering (Intel graphics)"
date: 2012-11-24
forum: Multimedia Software
---

### Post by ArsThaumaturgis on 2012-11-24
I'm having trouble with some graphical glitches, and and am hoping that someone will be in a position to help me:

Under Ubuntu 11.10, when developing with the Panda3D engine, I have occasional distorted/improperly rendered triangles (often stretched to cover large portions of the screen).

Under Ubuntu 12.04, when attempting to play various 3D games via Wine, I've experienced a variety of graphical issues, including:

[LIST]
[*]Distorted/improperly rendered triangles, as described above.
[*]Significant performance issues when a GUI is showing, but not otherwise.
[*]The games failing to detect any graphics devices, and so refusing to start.
[/LIST]
Not all occur in all games, but I seem to have trouble with rather more games than I manage to get to run, including, as I recall, games that Wine's AppDB indicates should run well.

The games could be Wine issues, but the number and variety of games that I'm having trouble with inclines me to think that the problem lies elsewhere, or otherwise is a matter of interactions between Wine and some other element.  The issue with Panda3D's rendering seems to support this, since this should have no real interaction with Wine.

Panda3D aside, I don't think that any of the games in question were terribly recent - indeed, some were fairly old (the one that exhibits the GUI issue comes from 1999, I believe).

At least some native Linux and DosBox-run games that use 3D rendering seem to be fine, including D1X-Rebirth (an engine for the playing of Descent) and Magic Carpet (native and DosBox respectively), I believe.

I'm using the "Glasen" Intel driver; if my reading of Xorg.0.log is correct, the appropriate versions do seem to be being loaded.

My system:
Gigabyte Q2005 (a netbook)
CPU: Intel Atom N550
Graphics: Intel GMA 3150
Memory: 2GB
OS: Ubuntu 11.10 and Ubuntu 12.04

(The integrated video device isn't wonderful, but it should be able to at least handle basic graphics; the fact that it works for some applications seems to support this.)

---

### Post by ArsThaumaturgis on 2012-11-30
*bump*

Any suggestions?  I'm still somewhat new to the technical side of Ubuntu, so please forgive me if I'm missing something obvious...

---

### Post by ArsThaumaturgis on 2012-12-04
*Final bump for this topic, I intend*

---

