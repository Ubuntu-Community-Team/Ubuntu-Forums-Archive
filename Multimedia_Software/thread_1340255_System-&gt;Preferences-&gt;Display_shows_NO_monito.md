---
title: "System-&gt;Preferences-&gt;Display shows NO monitors"
date: 2009-11-28
forum: Multimedia Software
---

### Post by timkoop on 2009-11-28
Hi everyone.

In my System->Preferences->Display, which pops up the "Display Preferences" window, I would like to click on my monitor and select a different screen resolution.  However, there aren't any monitors to click on, and the "Monitor" section of the window is greyed out.

Is there a way to get this working?  Perhaps there is a different program to configure the screen?  Do I need to change my driver? (If so, how?)

My video card has two heads but I'm only using one.

If I need to, I can configure my X11 conf file by hand, but I would prefer not to do that.  Gui is just better.

A lspci -v shows this: (I don't know what it means, besides the obvious make and model)

[FONT="Courier New"]01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
	Subsystem: C.P. Technology Co. Ltd Device 2072
	Flags: bus master, stepping, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at f0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at d800 [size=256]
	Memory at ef000000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at effe0000 [disabled] [size=128K]
	Capabilities: [58] AGP version 2.0
	Capabilities: [50] Power Management version 2
	Kernel modules: radeonfb[/FONT]

Thanks!

---

### Post by pi4r0n on 2009-11-28
Does it also happening when you type **gnome-display-properties** in your terminal ??

---

### Post by timkoop on 2009-11-28
> **pi4r0n said:**
> Does it also happening when you type **gnome-display-properties** in your terminal ??

Yes it's the same.  No monitor, and Monitor settings greyed out.

---

### Post by timkoop on 2009-11-29
Anyone else have any ideas?

---

### Post by pi4r0n on 2009-11-30
Have a look at [this one]("http://ubuntuforums.org/showthread.php?t=1283365")

---

