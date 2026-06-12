---
title: "Blocky or flickering video playback on ATI Radeon HD 3850"
date: 2008-08-10
forum: Multimedia Software
---

### Post by filburt1 on 2008-08-10
I have Compiz enabled and working just fine on Ubuntu 8.04 (32-bit) with an ATI Radeon HD 3850 using the latest 8.7 ATI official drivers. fglrxinfo says:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3850
OpenGL version string: 2.1.7412 Release
```
Video playback works in Totem fine, although if I make the video full-screen or any bigger than default, it's blocky like it's being resized using a nearest neighbor algorithm. If I try to play it in VLC using OpenGL output, it flickers wildly but strangely plays fine and at higher quality when full screen.

I've searched and found this is a very common problem for ATI cards but none of the fixes I've tried have worked. After each change, I run sudo aticonfig --input=/etc/X11/xorg.conf and restart X via Ctrl-Alt-Backspace.

I'm dual-booting with Vista and videos play back fine there, also using the 8.7 drivers.

I've attached my xorg.conf. Any suggestions?

---

