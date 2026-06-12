---
title: "Pitch shift trouble with audacity"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by King Donko on 2007-03-12
I have recently installed audacity through the add/remove app util, and it works great as long as I don't play other tracks while recording. (Makes it hard to synch tracks.)

When I try to record while other tracks play, the recorded track plays back at the same tempo, but with the pitch shifted waaaay down. I would try installing rosegarden or ardour, but I'm not quite linux-savvy enough to figure out how. (I'm completely new to Linux as of about 3 weeks ago.) Any help would be greatly appreciated.

I think the version of audacity I have is 1.2.4b-2ubuntu2, but when I try to check in the "help->about audacity" it shows boxes instead of characters.

---

### Post by King Donko on 2007-03-15
A friend of mine figured this out for me, thought I'd post it in case anyone else has the same problem. 

Go to preferences --> I/O,  change the # of channels from {1 - Mono} to {2 - Stereo}. My input only runs into the left channel, but it sounds like it's supposed to.

---

