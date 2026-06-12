---
title: "[SOLVED] GeForce FX 5200, mplayer, xvideo"
date: 2008-06-11
forum: Multimedia Software
---

### Post by tacutu on 2008-06-11
After 2 days of searching the forums I couldn't find an answer... so here I go:

on my old(ish) Nvidia card GeForce FX 5200, with restricted drivers enabled, no compiz, if I want to change the contrast / brightness in mplayer I get:
"Video attribute 'brightness' is not supported by selected vo & vd"

(I can still make it work with -vo gl2, though)

The only thing I found on the web is that newer Geforce cards don't contain hardware overlay support anymore. However, my card is older and it *has worked* in the past (Suse and other distros)

Any ideas? Should I try to install an older driver?

thanks in advance

---

### Post by tacutu on 2008-06-11
problem solved by adding:
```
Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```
into xorg.conf

---

