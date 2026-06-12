---
title: "movie players crash when I try to play movies"
date: 2010-05-10
forum: Multimedia Software
---

### Post by davidwillis on 2010-05-10
I can't play movies when I have browsers open.  I am not sure if it is the browser, or what.  I ran totem, and vlc in a terminal, and it says insufficient resources when I try to open a movie (see snapshot).

I also took a snapshot of my system monitor.  I am not sure what resources it is talking about?

---

### Post by davidwillis on 2010-05-10
This seemed to fix it for totem.

> Confirmed: the command is gstreamer-properties.

I went to the video tab, I selected "Default Output -> Plugin: X Window
System ( No XV )," and now works fine with Totem.
Only for totem. Not for mplayer neither VLC. Then, is reconfirmed that the
point is in the video output selected.

found [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/111257]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/111257")

---

### Post by davidwillis on 2010-05-10
the problem I do have with this is that it uses a lot of cpu to run.  I attached a snapshot you see that big spike up, that is when I started playing a movie.

---

