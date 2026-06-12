---
title: "Problem with mplayer"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by Hullon on 2007-11-07
When I start mplayer the default screensize for all movies, regardless of resolution looks like this: [http://img140.imageshack.us/img140/3326/screenshotxl3.jpg](http://img140.imageshack.us/img140/3326/screenshotxl3.jpg)

What could be the problem?

---

### Post by trak87 on 2007-11-07
You could try going in Preferences and changing the video driver. If you are using a restricted video card driver you should try gl or gl2, otherwise try xv or x11.

---

### Post by Hullon on 2007-11-07
There's only one driver present in the list, I have an ATI video card.

---

### Post by trak87 on 2007-11-07
Drop to a terminal window and run the video from there: "mplayer movie.avi" and see what you get. Then you can play with the video options there: "mplayer -vo xv movie.avi" or "mplayer -vo gl movie.avi" etc. See "man mplayer" for more options.

---

### Post by Hullon on 2007-11-07
That worked, thanks alot!

---

### Post by dashnak on 2007-11-07
You could also try and install smplayer, it's a frontend for mplayer.
My mplayer also does this, but with smplayer, I don't have a single problem.
It uses qt, but if you install from their repo and not from ubuntu repos, you don't have to install half of KDE, just qt support. It works great.
This is the repo:
deb [http://ppa.launchpad.net/themono/ubuntu](http://ppa.launchpad.net/themono/ubuntu) gutsy main universe

---

