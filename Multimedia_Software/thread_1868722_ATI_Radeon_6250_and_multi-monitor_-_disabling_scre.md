---
title: "ATI Radeon 6250 and multi-monitor - disabling screen cloning in console mode"
date: 2011-10-24
forum: Multimedia Software
---

### Post by Aesso on 2011-10-24
I recently replaced my two GeForce video cards with a single card with an ATI Radeon chipset so that I could connect my three monitors on a single card. This is one of those EyeFinity cards that has two DVI ports, HDMI, and a DisplayPort. I have three DVI monitors, one of which is connected to the DisplayPort with an active adapter. Now I'm finally rid of the shackles of Xinerama (which prevented me from running Compiz and Unity3D). Installing the proprietary driver ([FONT="Lucida Console"]fglrx[/FONT]) and configuring it using ATI's Catalyst utility was a cinch. I finally have a unified desktop **with** compositing!

I'm now experiencing an annoying hardware issue which isn't really an Ubuntu or Linux issue; nonetheless, I was hoping somebody here might know how to fix it. For some reason, my video card insists on cloning two of the displays during startup (from POST through Ubuntu boot-up until X11 starts). In the past when I've had this issue (cloning or the BIOS screens simply appearing on the wrong screen), I'd managed to "force" a single output by disconnecting all the monitors from the video card(s) except the primary, powering down, switching the computer back on, waiting for X to start, plugging the monitors back in, and the primary would stay put. With this card, my attempts yield only temporary results, and the cloning immediately returns the next time I return to console mode (such as during a restart/shutdown of Ubuntu or Ctrl-Alt-F1). 

The ATI Catalyst utility only seems to configure settings for the X server. Is there some kind of setting to "force" Ubuntu to only output to **one** of the monitors (the center one) during bootup or when using console mode? 

Is there a way to force the *card* to only output to one monitor when it's in low-level VESA graphics modes? Stuff like this makes me long for the days when you could set the jumpers yourself and be done with it! :) Thanks in advance.

---

### Post by Aesso on 2011-10-29
bump

---

