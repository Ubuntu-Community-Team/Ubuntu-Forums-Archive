---
title: "Auto-Run a DVD/ Change Program Default"
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by concerto on 2007-12-15
I would love to Find out where I can go to Read about how to Auto-run a DVD so when I put a DVD in my drive Ubuntu Automatically plays or runs a program every time I insert that type of disk.

Ultimately I would like my computer to auto-run movies and I would love to learn how to set VLC media player to be my default player.


There is no information for this problem  in the ubuntu help file.  and I can't find anything like this on this Post but this has to be a common problem.  Am I searching incorrectly?

Thank you for your time.

---

### Post by Krusader3z on 2007-12-15
You are going to need the appropriate things installed before you can play DVD's

I did this earlier today and now when I pop in a disk, it autoruns in Mplayer

[http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux)

---

### Post by fenian on 2007-12-15
You can do this with xine,first install xine from a terminal type...

> sudo apt-get install xine-ui

then go to the sytem menu and choose removable drives and media,click the multimedia tab and under Video DVD discs paste the following in the command box....

> xine -pfhq --no-splash dvd:// 

the dvd will open fullscreen.

---

