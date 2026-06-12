---
title: "VLC Fullscreen Question"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by dljesse on 2007-09-09
When I try and use fullscreen on VLC, the taskbar still shows on the bottom of the screen, and still appears in a box, what can I do to fix this?

---

### Post by nkessler2000 on 2007-09-09
You can try the "Alternate Fullscreen" setting. 

Go into the Settings --> Preferences menu
Expand Video --> Output Modules
Check the Advance Options box near the bottom right

You're probably using the XVideo, X11, or OpenGL module. Figure out which one, go into the settings for that module, and click the Alternate Fullscreen box. Click save and restart VLC. Should do the trick. If not, try a different output module.

---

### Post by dljesse on 2007-09-09
How do I go into the setting for a module?

---

### Post by nkessler2000 on 2007-09-09
Did you go into Preferences? See the little arrows on the left? Those indicate there's a dropdown list. Click the arrow next to Video, then click the arrow next to Output Modules. Next click the output module whose settings you wish to edit. 

Make sure the "Advance Options" box on the bottom right is checked, or you won't see the options you need.  

You can check and see which output module you're using by clicking Output Modules under video. It might be set to default, which I think is Xvideo. Mine is set to OpenGL

---

### Post by dljesse on 2007-09-09
I can't find where to click "Alternate Fullscreen", I have the drop down menu where I can choose between default, opengl and xvideo.

---

### Post by nkessler2000 on 2007-09-09
Okay, I made a screenshot. Hopefully this will help

[http://img260.imageshack.us/img260/5676/screenshotew4.jpg](http://img260.imageshack.us/img260/5676/screenshotew4.jpg)

---

### Post by graabein on 2008-05-12
I finally have two separate xscreens. One for my monitor (0) and one for my television set (1). I've tried both alternate fullscreen mode and switching X11, XVideo adaptor and screen for fullscreen mode between 0 and 1. 

Any ideas?

---

