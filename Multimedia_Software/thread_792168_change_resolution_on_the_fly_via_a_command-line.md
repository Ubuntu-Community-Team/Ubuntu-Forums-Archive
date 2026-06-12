---
title: "change resolution on the fly via a command-line"
date: 2008-05-12
forum: Multimedia Software
---

### Post by mboisson on 2008-05-12
Hello,
I can change my screen resolution on the fly via the preference menu. I would like to be able to do the same from command line. The problem is my hardware can't play movies in full resolution. I would like to create a script to change the resolution to 1280x720 when I open VLC and set it back to 1920x1080 when it closes. How can I do that ?

Thank you

---

### Post by mboisson on 2008-05-13
I found the solution, with the xrandr command :

xrandr --output default --mode 1280x720

xrandr --output default --mode 1920x1080

---

