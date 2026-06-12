---
title: "[SOLVED] Intel 915GM: Glitched 3-D"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by JWCBBDL on 2007-12-21
I want to say first of all that I am having no apparent problems with SCREEN RESOLUTION using the 915GM chipset (this seems to have been a common problem).  I am running at the native 1280x800 24-bit resolution just fine.

My problem occurs when I run a program that uses 3-D graphics (I presume that this is OpenGL).  I understand not to expect outstanding performance from integrated graphics, but here, polygons seem to be rendered in the wrong order, something which I have never seen before.  Screenshots of the "Planetary Gears" screensaver demonstrate this:

[[IMG]http://img412.imageshack.us/img412/3317/screenshotscreensaverprlf3.th.png[/IMG]](http://img412.imageshack.us/my.php?image=screenshotscreensaverprlf3.png)[[IMG]http://img136.imageshack.us/img136/9062/screenshotscreensaverprdm0.th.png[/IMG]](http://img136.imageshack.us/my.php?image=screenshotscreensaverprdm0.png)

Are there any additional drivers or packages needed to fix this?  Is there some configuration that needs adjustment?

The xorg configuration program points out that some graphics cards and chipsets do their best 3-D rendering only at certain resolutions and color depths.  I am running at my monitor's native resolution, but in 24-bit color (whereas Windows uses 32-bit color).  I understand that the difference between 24-bit and 32-bit color is merely either zero padding or alpha values, but could this difference possibly be responsible for the flawed performance here?  I understand that X is capable of both types of 32-bit color depth; how do I configure this?

Interestingly, Planetary Gears works fine in its small window in the screensaver configuration applet:

[[IMG]http://img137.imageshack.us/img137/9361/screenshotscreensaverprtn2.th.png[/IMG]](http://img137.imageshack.us/my.php?image=screenshotscreensaverprtn2.png)[[IMG]http://img148.imageshack.us/img148/9850/screenshotscreensaverprga3.th.png[/IMG]](http://img148.imageshack.us/my.php?image=screenshotscreensaverprga3.png)

Any help that can be provided would be greatly appreciated.

---

### Post by JWCBBDL on 2007-12-21
This problem occurs when full-screen previewing all of the 3-D screensavers, not just Planetary Gears.

Yet, as I discovered completely by accident, Planetary Gears and all of the other 3-D screensavers render just fine when the screensaver actually runs (as opposed to the "preview" function).

Conclusion: OpenGL works fine on my system; this is probably a bug in the screensaver configuration applet, which I will report.

Case closed.

---

