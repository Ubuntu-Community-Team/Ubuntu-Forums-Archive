---
title: "OpenGL rendering bug"
date: 2007-08-20
forum: Multimedia &amp; Video
---

### Post by bytesmythe on 2007-08-20
Hello all,

I have a laptop with an Intel 945GM graphics chip. Whenever I view OpenGL screensavers in the little preview window, they all work fine, but many of them look hideous in fullscreen mode.  There are a number of problems, but the biggest one has to do with the Z plane. Others include jagged edges on smooth surfaces and problems with reflections and shadows.

I've searched the forums and on google, but the only problem I keep hearing about is either related to the chipset's resolution (I'm using the new xserver), or large chunks of the screen don't render, which isn't happening with mine.

I've included a few descriptions of specific screensaver issues below and added screenshots of "Queens" and "Planetary Gears". If anyone can help with this, I'd appreciate it.

**UPDATE**

I accidentally left an OpenGL screensaver selected ("Planetary Gears" as it happens) and when it activated, the screensaver looked perfectly normal. These bugs only show up when you look at the fullscreen preview. Perhaps this is a gnome bug instead?

-- bytesmythe




"Queens" and "Endgame"
mini preview: looks normal
fullscreen: The reflections appear on all the squares, not just the shiny ones. The reflections protrude over the edge of the board. The shadows look like stuck together blobs.


"Gears"
mini preview: looks normal
fullscreen: When the gear system rotates, the gear in back is still on the front of the screen. Shadows are too harsh.

"Planetary Gears"
mini preview: looks normal
fullscreen: The "mounting bracket" in the center is in the front of the Z plane, so it's always drawn over the gears. When the gear system rotates, the gear in back is still on the front of the screen. Shadows are too harsh.


"Flying Toasters"
mini preview: looks normal
fullscreen: The toasters are "see through", i.e., you can see the bread and empty slots through the sides of the toasters. The toaster wings are rendered over the toaster, so the entire wing is visible.


"Bubbles"
mini preview: looks normal
fullscreen: Lighting is harsh, not blended.


"GLKnots" and "GLText"
mini preview: looks normal
fullscreen: Any spot with a smooth curve in the surface looks like microscopic slices have been cut out of it.


"GLSnake"
mini preview: looks normal
fullscreen: The snake segments are all drawn on top of each other, so you can't actually tell what the shapes are.

"JigglyPuff"
mini preview: looks normal
fullscreen: Rounded parts have weird shadows in them. Rendering is kind of slow.  Very jagged edges.

"Lattice"
mini preview: looks normal
fullscreen: Lack of proper Z plane rendering makes this one a complete mess.  Very jagged edges.


"LavaLite" and "MirrorBlob"
mini preview: looks normal
fullscreen: Black patches on edge of blob where redrawing isn't done properly. Very jagged edges.


"Moebius"
mini preview: looks normal
fullscreen: Ants in the back are visible in front of the loop.

---

### Post by clubsoda on 2007-11-20
Ah, I should have added [mine](http://ubuntuforums.org/showthread.php?t=618430) to your thread here.

Using *PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)* to a *VGA compatible controller: Matrox Graphics, Inc. MGA G550 AGP (rev 01)* here, but I usually keep my antiquated chipsets on the low.  8-[

---

### Post by quanumphaze on 2007-11-20
I have the same problem. Gears, Toasters, Queens, etc. all show up funny in full screen preview. It might be intel945 related.

The **Cube Gears** plugin for Compiz also has the same problem.
I can't find a solution on these forums, so I'll have to put up with the ugly previews.

---

