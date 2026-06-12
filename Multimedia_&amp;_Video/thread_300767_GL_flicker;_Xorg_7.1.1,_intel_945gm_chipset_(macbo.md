---
title: "GL flicker; Xorg 7.1.1, intel 945gm chipset (macbook); i810 driver"
date: 2006-11-16
forum: Multimedia &amp; Video
---

### Post by est on 2006-11-16
My macbook has an intel 945gm integrated graphics and I'm using the i810 driver in Xorg 7.1.1ubuntu6.1.

My problem is intense flickering with openGL when AIGLX (with beryl) is enabled with screensavers, glxgears, games, (sigh) google earth and mplayer's GL video output. They all suffer the same problem. Black rectangles appear -- regions are not refreshed quickly enough. It looks terrible.

According to glxinfo (and Xorg logs) DRI is enabled and running fine, and the only warning messages I get are:
libGL warning: 3D driver claims to not support visual 0x5b

UPDATE 1: If I disable AIGLX and Composite, the warning goes away as does the flickering.

UPDATE 2: If i enable AIGLX and Composite, but kill beryl, the warning remains but the flickering disappears. Will inform Beryl people.

My question is of course, anyone know what's causing this flickering problem and how to solve it?

---

### Post by est on 2006-11-16
I've posted a bug to the beryl project. ([for reference]("http://bugs.beryl-project.org/trac/ticket/971"))

In the meantime, I hacked this workaround up: save it as rungl somewhere in the path (~/bin is good).

```

#!/bin/sh
killall beryl; metacity & $*; beryl &
```

Now if you run `rungl <program and arguments>' beryl will be stopped, metacity run and then the program, with arguments, will be run. Once the program is finished, beryl will be restarted. I've edited menu items to run e.g. "/home/edd/bin/rungl /opt/google-earth/googleearth" and it's not ideal but better than before.

---

### Post by kwaanens on 2006-11-17
I get the same on my Dell Inspiron 9300 with an ATI x300 card. Killing beryl does the trick. (Although Googleearth is painfully slow on Ubuntu, compared to XP on the same hardware.

- Ketil

---

### Post by est on 2006-11-18
Cheers Ketil, 
By the way there's the same problem with beryl svn, so don't bother going down that road.
Have you tried compiz? I'm unable to get it running at all, both official and 3rd party packages.

---

### Post by kwaanens on 2006-11-19
> **est said:**
> Have you tried compiz? I'm unable to get it running at all, both official and 3rd party packages.

No, I haven't. I'm settling on Beryl for now, it seems to be an acceptable choice. And for the bug, Google Earth is getting old, so it's not really that big of a problem for me. And Totem seems to show at least DVDs just fine on my system.

---

### Post by jomtois on 2006-11-25
I have had the same flickering issue with Beryl and AIGLX.  I notice it a lot when activating an OpenGL screensaver such as Hufo's tunnel.  It seems to do with there being windows or changing items "behind" the screensaver and it interferes.  If I rotate the cube to an empty desktop with no windows on it, the screen saver runs relatively well with the only flickering being from a network montitor I have in the taskbar (so just a small box flickering).  However, if there are other windows on the screen, it flickers them through, especially if there is refreshing content in them (ie a konsole with top running).  It seems like it is fighting for a redraw with the OpenGL portion.

I haven't found any workarounds.

---

### Post by Offoffoff on 2008-03-29
I am interesting in it too. Hate that flickering in Google Earth.

---

