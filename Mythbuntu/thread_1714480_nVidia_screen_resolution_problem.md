---
title: "nVidia screen resolution problem"
date: 2011-03-25
forum: Mythbuntu
---

### Post by emunson on 2011-03-25
I solved my video tearing problem on my HD 5450 by replacing it with a G 210, I finally have video playback and sound all working, but the display is a little off.  The nVidia tool claims it has the monitor set to 1920x1080 (this is an LG 37" LED TV) but the display runs over all 4 edges screen.  So I cannot see anything that renders close to the edge.  What could be causing this?

---

### Post by LowSky on 2011-03-25
its called overscan if your using hdmi it can be fixed

gksu nnvidia-settings

look for overscan compensation and adjust slider to fit screen

---

### Post by utar on 2011-03-26
Most TVs stretch the picture by a small amount by default - don't ask me why.

Look for an option such as "full pixel" in your TV options which will disable the stretching.  

LowSky's solution will work fine, but it is better to get your TV to do it right itself.

---

### Post by emunson on 2011-03-29
The first problem was solved by setting the DPI properly.  I found how to do this by searching the forum (not just Mythbuntu).  Once that was set properly I could actually see the overscan slider.

---

### Post by Stray Wolf on 2011-09-26
> **emunson said:**
> The first problem was solved by setting the DPI properly.  I found how to do this by searching the forum (not just Mythbuntu).  Once that was set properly I could actually see the overscan slider.

This might help me but...how did you change the DPI?  Did you change it in natty or on your tv?  I'm running on a 52" Panasonic plasma screen.

---

### Post by emunson on 2011-09-28
I don't remember what actually worked for me, but here is what I have found searching

[http://ubuntuforums.org/showthread.php?t=1826948&highlight=nvidia+adjust+dpi](http://ubuntuforums.org/showthread.php?t=1826948&highlight=nvidia+adjust+dpi)

---

