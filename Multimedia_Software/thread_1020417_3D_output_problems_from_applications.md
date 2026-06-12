---
title: "3D output problems from applications"
date: 2008-12-24
forum: Multimedia Software
---

### Post by XeroxGUI on 2008-12-24
Whenever I run a program such as Armagetron Advanced or Project 64 under wine, I get messed up (to put it lightly) 3D graphics. I have an Intel graphics card on a Gateway MT6705 laptop. 

I think this all stems from a video problem I had months ago, where after plugging two monitors into said laptop, the resolution tool under GNOME misconfigured my card and had me in a low resolution and disabled compiz (yes, I run all sorts of compiz plugins as I've done with no problems for a long time). 

Well to solve it I had to reconfigure xorg to get compiz back and all, and somewhere between there and the upgrade from 8.04 to 8.10 I lost comprehensible 3D graphics in applications, yet compiz works.

here is some information:

My org.conf:
```

# --snip-- default comments here
Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```$ glxinfo | grep -i direct
```

direct rendering: Yes

```$ glxinfo | grep -i opengl
```

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061102 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.2
OpenGL extensions:

```glxheads displays spinning triangles, glxgears displays the gears flawlessly, but glxdemo displays an empty black window that outputs to standard output whenever it is "resized" or moved. I am at my wits end about this and need help! :confused:

Attached are demonstrations of the issues with Armagetron Advanced (opengl.png) and project 64 issues (legend of zelda OOT intro, loz.png). Both of these applications worked flawlessly before the reconfiguration, and other apps affected by the same issues are OpenArena, SuperTux, and Frets on Fire. Mainly a text/shading problem, and my Mac OS X Leopard (hackintosh) installation on this same machine plays halo flawlessly, so I know its not a hardware issue. 

Any Help is much appreciated!

---

### Post by XeroxGUI on 2008-12-24
bump

---

### Post by moises.ti on 2009-02-09
I am with the same problem. Have managed to resolve? Excuse the english, I'm Brazilian. I do not speak English.

Thank you.

---

### Post by Tuxoid on 2009-02-09
I am having a similar problem. All my 3d-dependant wine apps have garbled graphics ever since upgrading to ibex. In hardy, I wasn't using the i810 driver, I was using the intel, which worked fine in hardy. In ibex, it's buggered all my 3d wine graphics. Native 3d-dependant apps run normally, however.

I would suggest that anyone suffering a similar issue run glxdemo from a Terminal (as unfortunately, that's really the only way i know to get more detailed info), and post the output it produces.

Here's mine:

```
Resize event
Resize event
Redraw event
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 36 requests (33 known processed) with 0 events remaining.

```

I hope we can all fix this.

---

### Post by moises.ti on 2009-02-11
> **Tuxoid said:**
> I am having a similar problem. All my 3d-dependant wine apps have garbled graphics ever since upgrading to ibex. In hardy, I wasn't using the i810 driver, I was using the intel, which worked fine in hardy. In ibex, it's buggered all my 3d wine graphics. Native 3d-dependant apps run normally, however.

I would suggest that anyone suffering a similar issue run glxdemo from a Terminal (as unfortunately, that's really the only way i know to get more detailed info), and post the output it produces.

Here's mine:

```
Resize event
Resize event
Redraw event
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 36 requests (33 known processed) with 0 events remaining.

```

I hope we can all fix this.

	
I did the test you suggested, the return was equal.

```

XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 36 requests (36 known processed) with 0 events remaining.

```

---

