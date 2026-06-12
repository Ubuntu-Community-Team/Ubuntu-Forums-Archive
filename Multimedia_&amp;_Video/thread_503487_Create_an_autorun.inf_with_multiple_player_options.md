---
title: "Create an autorun.inf with multiple player options... possible?"
date: 2007-07-17
forum: Multimedia &amp; Video
---

### Post by southernman on 2007-07-17
Is it possible to create a single autorun file that will look for a variety of media players?

This is what I have, which I believe will autoplay the video on media player:

```

[autorun]
open=mplayer2.exe /play /close \<filename>.avi

```

Would I just add various players to the list like:

```

[autorun]
open=mplayer2.exe /play /close \<filename>.avi
open=vlc.exe /play /close \<filename>.avi

```

or would I have to create seperate files for each player?

#2- How would you do so for the linux platform?

*wonders why I feel stupid for asking such...*

---

### Post by pressed on 2008-03-28
southernman, did you ever figure this out?

---

### Post by southernman on 2008-04-26
No pressed, I did not figure this out.

---

### Post by p0ck3t5 on 2008-05-20
you might try using the shellexecute function of the autorun.inf file. this would open your document (music file, whatever) with the default application for that file extension.

 more information is available at [http://msdn.microsoft.com/en-us/library/bb776823.aspx](http://msdn.microsoft.com/en-us/library/bb776823.aspx)

---

