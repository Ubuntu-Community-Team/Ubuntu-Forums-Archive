---
title: "Disappearing MPlayer/VLC"
date: 2009-10-02
forum: Multimedia Software
---

### Post by waldo_phill on 2009-10-02
Whenever I attempt to play a movie whether it be a DVD or avi as soon as the programs attemt to load the movie the program closes out. I have not been able to find a solution every after following this [howto]("http://ubuntuforums.org/showthread.php?t=766683") any help would be appriciated.

---

### Post by frontrow on 2009-10-17
I had a similar problem.  Try this:

from the terminal, type  gstreamer-properties

this should open a window called Multimedia System Selector

select the video tab

change default output to X Window System (no Xv)

close the window

That should do 'er.

---

