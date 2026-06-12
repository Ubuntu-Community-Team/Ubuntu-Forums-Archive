---
title: "Playing CDs"
date: 2011-11-18
forum: Multimedia Software
---

### Post by buddy56 on 2011-11-18
I have an old PC that i have been running xubuntu on for about a yrs. Now i can't play CDs, they will not mount,read or anything. My DVDs will mount and play great. i've reinstalled everything but didn't work. Please help I love my Music.

---

### Post by Toz on 2011-11-18
Which version of xubuntu? If you go to Settings Manager -> Removable Drives and Media -> Multimedia tab, is "Play audio CDs when inserted checked" and if so, which application is listed?

---

### Post by buddy56 on 2011-11-18
1010 xubuntu and Exaile

---

### Post by buddy56 on 2011-11-18
Everything worked great untill 3 days ago. Now i get (no URI handler implemented for cdda) when i try to play my CDs. Its like its not reading my dvd/cd player but it has to if its working with dvds.Been using Exaile but its not working with any music player i've tried.

---

### Post by Toz on 2011-11-18
What updates happened 3 days ago? I believe you can review updates in the Software Centre or at /var/log/apt/history.log.

Was gstreamer updated? See: [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/435035]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/435035") (the bug report is dated, but the symptoms are similar).

Also, an interesting thread: [http://comments.gmane.org/gmane.linux.distributions.trisquel.user/5408]("http://comments.gmane.org/gmane.linux.distributions.trisquel.user/5408").

---

### Post by buddy56 on 2011-11-18
Thanks Toz, you got me thinking in the right direction. Had to play with gstreamer.

---

### Post by Toz on 2011-11-18
If you don't mind, what was the final solution? In case someone else comes across this thread.

---

