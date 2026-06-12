---
title: "rhythmbox shuffle plays some songs frequently"
date: 2009-12-31
forum: Multimedia Software
---

### Post by autonomy on 2009-12-31
I've noticed how rhythmbox will play certain songs on shuffle everyday and sometimes twice a day, and it gets to me because I have six days worth of music; and there are lots of songs I haven't heard; but every now and then rhythmbox has to play the same old songs over and over. I know random algorithms can seem less random sometimes, but this has become very noticeable.

---

### Post by bt101 on 2010-01-10
I know what you are saying.

I only looked at a few players till I found one that properly performs shuffle.

With Amarok, when you hit shuffle, you can see (in front of your eyes) that the entire play list is shuffled.  Now, when you begin playing, it will go through the now shuffled list.  It does not jump around and potentially repeat the same song.  Also, you are now dealing with a "static" list where you can "see" the order of the songs and you know what you are getting if you go forward/backward.  Seems simple to me and I don't know why every player doesn't do it.

The knock on Amarok is that it is a bit of a big download/install.
It has a nice on-screen-display as well.

---

### Post by autonomy on 2010-01-13
I'm about to switch to that player if Rhythmbox doesn't quit automatically selecting the first menu option, Add to Play Queue, everytime I right-click a song! :mad:

---

### Post by aliciapg on 2010-02-07
[Launchpad bug report]("https://bugs.launchpad.net/rhythmbox/+bug/20032")
Others have this problem too (like me). T-T

Here is an [old post]("http://ubuntuforums.org/showthread.php?t=127008") about this problem, but you can't use the same fix. The gconf-editor no longer has these options and I found that manually changing it in the xml file doesn't work because the file refreshes after a song finishes playing.

But I did find these settings were once available ([on this site]("http://www.last.fm/group/Rhythmbox/forum/8096/_/288791")), who knows when they will actually allow you to use them with the interface...:

linear-loop: ordered playlist and loops back to the beginning
linear: ordered playlist, but stops when finished
random-by-age-and-rating: random playlist, preferring songs that haven't been played in a while or have a high rating
random-by-age: random playlist, preferring songs that haven't been played in a while
random-by-rating: random playlist, preferring higher rated songs
random-equal-weights: random-ordered playlist where all songs are played in equal amounts
shuffle: random

BUT, when you have **shuffle** selected, "**shuffle**" is used. When you have **shuffle and repeat** selected, "**random-by-age-and-rating**" is used. So sort of helpful.

---

