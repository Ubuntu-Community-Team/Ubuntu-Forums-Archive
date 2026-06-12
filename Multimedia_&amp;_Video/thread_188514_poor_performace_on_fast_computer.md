---
title: "poor performace on fast computer"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by Schalken on 2006-06-04
**Short story:**
Why does glxgears run at 0.2fps on a 3Ghz CPU with 1GB of RAM and integrated graphics?

**Long story:**
Im not going to go through my month-long experience of configuring Ubuntu, but basically it boils down to this:

I have a 64bit Celeron D 3.06Ghz with 1GB of RAM and on board SIS 661FX video. I am using Ubuntu 6.06 32bit so flash, WMVs, cedega and my printer drivers work. I am using the SIS video driver from winischhofer.com (who apparently maintains the SIS video drivers for linux)(these made no difference).

Currently there is a pretty severe performace problem regarding the graphics not only in OpenGL, but in Ubuntu in general. Windows take a second or two to minimise/maximise/resize etc and while typing sometimes the letters have a delayed appearance. When sound effects play there is a 1 second pause in them. Blender runs at about 5fps. :confused:

When I run glxgears (the OpenGL test) it runs at about 50 fps (or so it looks) for 2 seconds and then dies; it looks like its running at 0.2 fps (the gears move slightly/a frame passes every few seconds). While glxgears is running the Xorg process is using 98% of the CPU power. (Is that normal? Is that where the bottle neck is?)

I should note that I was using SUSE 10.1 for a while and it ran perfectly fine out of the box. I was using screensavers and playing BZflag without problems.

Right now I have no idea why Ubuntu is running sluggishly on a recently purchased computer, while SUSE ran fine. ](*,) I'm sure the drivers I have are the only ones that are avaliable for Linux. Does anyone have any ideas why Ubuntu would run sluggishly, as to where the problem/bottleneck would be (drivers? xorg config? opengl config?), or have had something similar happen to them before?

---

### Post by JoWilly on 2006-06-04
Are you sure suse was using the same drivers ?

Do you have, or can you get a hand on (maybe reinstall suse on a spare partition to get the xorg.conf file), a copy on the xorf.conf file that was working in suse ?

---

