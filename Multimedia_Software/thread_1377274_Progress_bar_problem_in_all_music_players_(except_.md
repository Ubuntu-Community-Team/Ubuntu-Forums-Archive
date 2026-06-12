---
title: "Progress bar problem in all music players (except VLC of course)"
date: 2010-01-10
forum: Multimedia Software
---

### Post by stark222000 on 2010-01-10
In all music players I have a problem with being able to fast forward/skip through music. in Rhythmbox it shows all the songs as having a time of 0:00 although it plays them (and when i put the songs on my iPod they all said 0:00 there too but on other computers and such it says the right time). This also leads to me not being able to skip through the music.

so I got Banshee to see if it happened there and the same story. So i got Exaile and it shows the progress slider as moving and displays all the correct time so i thought everything was fixed but i still can't skip through the music at all. VLC of course works fine as it always does but does anyone know why this is? any help is greatly appreciated.

---

### Post by stark222000 on 2010-01-10
anything?

---

### Post by tobz1000 on 2010-02-10
I'm having the exact same problem. I recently installed and uninstalled KDE, if that could somehow be a cause. Otherwise I have no idea.

In other words, bump.

---

### Post by tobz1000 on 2010-02-10
I had to reinstall gstreamer-plugins-ugly to play WMAs, and this seemed to fix it! Try reinstalling gstreamer0.10-ffmpeg and plugins-base/good/ugly.

---

### Post by Izym on 2011-02-18
> **tobz1000 said:**
> I had to reinstall gstreamer-plugins-ugly to play WMAs, and this seemed to fix it! Try reinstalling gstreamer0.10-ffmpeg and plugins-base/good/ugly.
It seems to have solved my problems. Thanks a lot!

---

