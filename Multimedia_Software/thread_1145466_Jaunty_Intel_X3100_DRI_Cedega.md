---
title: "Jaunty Intel X3100 DRI Cedega"
date: 2009-05-01
forum: Multimedia Software
---

### Post by loneowais on 2009-05-01
I'm have an Intel X3100 Gfx Card on my notebook. We all know Jaunty has issues with it but I've fixed them by installing the latest kernel.

The problem is that Cedega fails the two video test (OpenGL Direct Rendering and 3D Acceleration). It says that Direct Rendering is not ON.

But my x.org has to say something else

> 
Section "Device"
        Identifier  "Card0"
        Driver      "intel"
        Option "DRI" "true"
        Option "AccelMethod" "EXA"
        Option "MigrationHeuristic" "greedy"
        Option "ExaNoComposite" "false"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

I can verify it by issuing  **glxinfo | grep -i direct**
> **direct rendering: Yes**

How can I fix this?

Native linux games like Urban Terror, Assault Cube and even Compiz-Fusion run without a glitch.

---

