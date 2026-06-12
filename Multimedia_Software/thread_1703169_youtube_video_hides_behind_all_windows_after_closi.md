---
title: "youtube video hides behind all windows after closing firefox tab"
date: 2011-03-08
forum: Multimedia Software
---

### Post by patapra on 2011-03-08
after watching a youtube video and closing the tab (or entirely closing firefox for that matter), a snapshot of the video hides in the background of all my windows. seems to reveal itself most in the color black. for instance, i can see parts of it in each letter of this post and see the entire video in a terminal (see attached image - sorry, it doesnt show up in screenshots. had to use my iphone to take the picture).

any ideas or things i can post to help debug?

---

### Post by vjkeito on 2011-06-24
I have the same issue also.  I can fix it by opening gstreamer-properties and changing the video setting to "X Window System (No Xv".

This is obviously some sort of bug.  Not the best fix, but it works.

---

