---
title: "mythbuntu-lircrc-generator creates duplicate entries in mythtv"
date: 2012-09-10
forum: Mythbuntu
---

### Post by SteveOllis on 2012-09-10
Hi all..

I've been beating my head on a double remote key entry issue. I have a pair of leadtek (DTV1000-T and DTV1000-S) cards and couldn't figure out why I was getting duplicate keypresses.

I had a look in ~/.lirc/mythtv, and there were duplicate entries for all buttons. Fortunately, it's an easy hack to find the top of the second lot of keys.
edit ~/.lircrc/mythtv
Find "button = KEY_0"
Find it again..
Cursor up 3 lines to the "begin" section
delete to the end of the file.

Without looking at the source Luke, I hypothesize that lircrc-generator is looking at the cards in the system, seeing they are both "devinput" cards, and generating two copies of the remote entries into one file.

Hope this helps someone else.

---

### Post by SteveOllis on 2012-09-10
something I forgot to mention.. 

This is occurring in ALL of the files that mythbuntu-lircrc-generator creates.. such as elisa, mplayer, etc.

---

