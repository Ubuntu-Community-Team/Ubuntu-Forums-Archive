---
title: "Dual monitor virtual screen very slow"
date: 2013-04-25
forum: Multimedia Software
---

### Post by jimbobboy on 2013-04-25
I am running 13.04 on a Compaq nc6320 laptop with Intel® 945GM x86/MMX/SSE2 graphics.  My second monitor is an HP L2208W with preferred resolution 1680 x 1050.  By default the display is mirrored at 1280 x 1024.  When I try to unmirror the screens and set resolution correctly I get 

"Requested size (2560, 1737) exceeds 3D hardware limit (2048, 2048).
You must either rearrange the displays so that they fit within a (2048, 2048) square."

A little searching revealed that I must create /etc/X11/xorg.conf and add

Section "Screen"
Identifier "Default Screen"
Device "Default Video Device"
SubSection "Display"
Virtual 2560 1737
EndSubSection
EndSection

With this in place, I can now extend the desktop across both screens with the correct resolution.  Only problem is that now graphics are extremely slow and jerky, even with all animations turned off.

Is there any way to fix this, or am I doomed to have EITHER normally fast graphics OR an extended desktop, but never both?

---

