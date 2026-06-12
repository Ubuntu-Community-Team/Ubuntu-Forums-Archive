---
title: "How to make screen resolution permanent?"
date: 2013-01-21
forum: Multimedia Software
---

### Post by glendavee on 2013-01-21
I'm running ubuntu 12.10, 64 bit. Recently my screen resolution changed to 1024x768 for no apparent reason. I have managed to go back to 1280x1024 by following these instructions :
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html")
However when I try to save changes by going to /etc/gdm/init as instructed, it doesn't exist. GDM isn't installed in 12.10?
Question - how do I make my changes in resolution permanent? Should I install gnome display manager and go from there or is there a better way?

---

### Post by glendavee on 2013-01-22
Problem solved by installing gdm and then editing the /etc/gdm/init/Default file

---

