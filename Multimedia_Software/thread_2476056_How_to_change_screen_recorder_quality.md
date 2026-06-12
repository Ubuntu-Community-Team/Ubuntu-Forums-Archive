---
title: "How to change screen recorder quality?"
date: 2022-06-15
forum: Multimedia Software
---

### Post by WHK on 2022-06-15
Have Ubuntu 22.04 and use native screen recorder. I see the video recorder button but have not a button to setting quality, the result and fps are very poor. Have a AMD Radeon gt 6800 xt, simple screen recorder works fine on xorg but ubuntu 22 and amd drivers use wayland and ssr is not working over wayland.

How to setting the fps and quality on native screen recorder?

---

### Post by TheFu on 2022-06-16
X programs often don't and won't work with Wayland.  

Screen recorders and some automation tools have long taken advantage of some long-known security problems with X11.  
The poor screen recording, that it doesn't work with nVidia GPUs, and that many other X/Windows dependent workflows are way many of us still use X11 and not Wayland.  Nearly all my work is performed running programs on other systems, but displaying the window on a less-than-great local desktop.

You know the solution.  Use X11 and simplescreenrecorder.  You could open a bug report with the gnome.org people which has been moving to Wayland. Hopefully, they will  say, " thanks for the test scenario so we can fix it."
There's an email link here: [https://help.gnome.org/users/gnome-help/stable/screen-shot-record.html.en](https://help.gnome.org/users/gnome-help/stable/screen-shot-record.html.en) for feedback.  Perhaps they will update the documentation with the magick incantations and which animals need to be sacrificed to modify the recording parameters in the massively hidden DB that Gnome uses for settings. I miss text config files - SOOOOOOO much.

Seems that the built-in Gnome screen recorder was created mostly for quick and efficient, not quality, recording.

---

