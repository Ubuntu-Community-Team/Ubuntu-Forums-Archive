---
title: "What is the best and newest mplayer version for maverick?"
date: 2010-08-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-08-01
I want to check if my problems with movies are from the mplayer or the fglrx driver.

Thanks in advance.

---

### Post by moviemaniac on 2010-08-01
the latest version is always found in the mplayer svn repo (that's what I use): svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer

(followed by the usual compilation process; there are many threads to be found on the ubuntuforums about configure options and needed dependencies)

---

### Post by Starks on 2010-08-01
Uh, the mplayer trunk is neither the newest or best.

Most mplayer devs and cool kids use the mplayer-build/mplayer.git fork to introduce new features and keep libraries up to date.

Here's a PPA that takes advantage of it: [https://launchpad.net/~ripps818/+archive/coreavc]("https://launchpad.net/%7Eripps818/+archive/coreavc")

Pay no mind to the CoreAVC instructions unless you want to.

---

### Post by moviemaniac on 2010-08-01
yeah, well, there are positive and negative sides to the mplayer-build thingy - personally I don't like it (too automated and unflexible) and stick with the svn repo. But then again I only update mplayer once a month or so as I rarely use it and pay closer attention to VLC and ffmpeg.

---

