---
title: "Banshee 1.2.1 -- No video"
date: 2008-09-21
forum: Multimedia Software
---

### Post by bark50 on 2008-09-21
I recently installed Banshee 1.2.1. in Hardy.  Playing videos, I can get sound put usually only see a black screen.  Occasionally I get the video, but it disappears when I go to full screen and stays gone if I go back to regular mode.  These are mostly wmv and flv I am trying to view.  They play fine in MPlayer and VLC.  Is there an easy solution for the complete idiot other than abandoning Banshee for another media player?  Thanks!

---

### Post by RobLoach on 2008-10-06
> **bark50 said:**
> I recently installed Banshee 1.2.1. in Hardy.  Playing videos, I can get sound put usually only see a black screen.  Occasionally I get the video, but it disappears when I go to full screen and stays gone if I go back to regular mode.  These are mostly wmv and flv I am trying to view.  They play fine in MPlayer and VLC.  Is there an easy solution for the complete idiot other than abandoning Banshee for another media player?  Thanks!

I believe this is because of GStreamer vs XINE. Try switching over to xine instead of gstreamer from synaptic and see if that fixes it.  Not entirely sure though....

---

### Post by RobLoach on 2008-10-15
Xine didn't do it. I'm still hitting the same problem.

---

### Post by bark50 on 2008-10-15
I got Banshee's video to work by doing the following:

1.Open up the terminal and type in (without the quotes) &#8220;gstreamer-properties&#8221;.
2.A box opens up called &#8220;Multimedia Systems Selector.&#8221;  Click on the video tab.
3.Where it says &#8220;Default Output Plugin:&#8221; select "X Window System (No Xv)".

This worked for me.  According to a post in the Banshee forum, doing this results in an increased CPU load.  ([http://www.nabble.com/Audio%2C-no-video-to18120808.html#a18120808](http://www.nabble.com/Audio%2C-no-video-to18120808.html#a18120808))  However, even before making this change, I noticed enabling Banshee's equalizer caused crackles and stutters in my music collection.  I finally just uninstalled Banshee entirely; there are enough good music and video players for my needs that I felt no need to hassle anymore with this player.

---

### Post by RobLoach on 2008-10-16
That did it! Thanks a lot.... "X Window System (No Xv)" worked perfectly.

The sound is crackling for you? It's fine here... Are you using the right gstreamer plugins? Check synaptic...

---

### Post by sd@ksu on 2012-06-01
thanks a lot

---

