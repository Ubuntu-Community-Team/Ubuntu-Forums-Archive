---
title: "VLC: Full screen stuck on 1 screen"
date: 2008-06-01
forum: Multimedia Software
---

### Post by relix on 2008-06-01
I've got a dual monitor configuration, using nvidia restricted drivers.

I can play video on both monitors, but when I want to view it full screen, it always goes full screen on the same monitor, regardless which screen the VLC window was on.

I deduced that this is because of a setting "Screen for fullscreen mode" under the XVideo settings, where I can set a number for the screen. 0 is my first screen, and 1 is the second screen.

Is there a way to make this dynamic? As in, it shows full screen on the screen the VLC window is on?

---

### Post by ishanaba on 2009-11-13
still have the prob

Go to terminal:
gstreamer-properties

a box will pop up, click the video tab
under output, choose "no xv" option for the plugin

---

