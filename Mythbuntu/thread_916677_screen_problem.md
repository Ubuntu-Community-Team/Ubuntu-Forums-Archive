---
title: "screen problem"
date: 2008-09-11
forum: Mythbuntu
---

### Post by spoky99 on 2008-09-11
During the installation of mythbuntu the screen don't show all the windows menu', and I must select the button under the menu without see it and often I restart the installation because I don't guess the button.
After the installation the graphic card is not recognised, in the menù of xfce (setting manager -> screen) I could only select a wrong resolution (widescreen 1280x800 instead of 1280X1024) and looking the xorg.conf is setting using vesa.
I try to use displayconfig-gtk and this configure in the right way the xorg.conf but wen I restart the gdm i see one of this two thing.
- the monitor is black and one message of my lcd monitor is show "input non supported"
- I see one part of the screen and using the mouse I could moove in all the screen but.. I'm not in able to see the entire screen. If I try to use the "setting manager" -> screen menu' I found only the 600x480 resolution available.

this is my lspci of the graphic card
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Intel Corporation 82852/855GM Integrated Graphics Device
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0000000 (32-bit, prefetchable) [size=128M]
	Memory at e4100000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at ac00 [size=8]
	Capabilities: <access denied>

and my lcd is one Acer AL1916C or AL1916Cs

I also try setting my lcd using displayconfig-gtk using a general lcd 1280x1024 or selecting all the Acer AL1916 but without solve the problem.

I partially resolved the problem of the screen, I copy the xorg.conf text of screen and monitor of another computer that work with the same monitor. Now xfce screen menu' display also the other resolution and screen of lcd is equal to the desktop screen, but xfce work in vga mode (don't use intel driver)

---

