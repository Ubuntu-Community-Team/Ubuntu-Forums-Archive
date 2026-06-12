---
title: "correct driver for the Radeon IGP 320M"
date: 2005-10-24
forum: Multimedia &amp; Video
---

### Post by herot on 2005-10-24
does anyone know what the best choice driver is for a Radeon IGP 320M video card?
im running a Compaq Evo N1015v with this video card and i am looking to increase performance and possibly get some GL ability as well, if possible...

my xorg.conf:

```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
        Driver          "radeon"
        BusID           "PCI:1:5:0"
        BoardName       "Radeon Mobility U1"
        Option "AGPMode" "4"
        Option "ForcePCIMode" "True"
        Option "EnablePageFlip" "True"
EndSection

```

---

### Post by mlomker on 2005-10-24
My last laptop had that card and getting 3D to work is difficult.  You basically have to compile your own patched kernel.  I decided to upgrade my machine instead of pursue it, but I did some research on it.  [Here's a link]("http://rzr.online.fr/docs/comp/gfxcard.htm").

---

### Post by enderson on 2005-11-26
[QUOTE=mlomker]My last laptop had that card and getting 3D to work is difficult.  You basically have to compile your own patched kernel.  I decided to upgrade my machine instead of pursue it, but I did some research on it.  [Here's a link]("http://rzr.online.fr/docs/comp/gfxcard.htm").[/QUOTE]

I'v just installed Ubuntu on my Compaq nx9005, it has a IGP 320M too.

I think I have 3D out of the box, 'cause I can see "Direct Rendering: Yes" in the output of glxinfo, is that enough to say I have 3d support ?


Edit: I forgot to say tha the driver I'm using on xorg.xonf is ati, and not radeon.

---

### Post by mlomker on 2005-11-27
[QUOTE=enderson]I think I have 3D out of the box, 'cause I can see "Direct Rendering: Yes" in the output of glxinfo, is that enough to say I have 3d support ?
[/QUOTE]

Sure, but there's a difference between hardware and software 3D.  In the case of the IGP320 it's not much, though, because that's a slow card.

---

