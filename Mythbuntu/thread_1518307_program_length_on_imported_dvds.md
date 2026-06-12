---
title: "program length on imported dvds"
date: 2010-06-26
forum: Mythbuntu
---

### Post by zapstrap on 2010-06-26
I've noticed lately that if I import a DVD, the program length shows as considerably shorter than the program actually is.  This is not a huge problem, but fast forwarding and reversing cause the position in the program to skip wildly all over the place.  Viewing the same program in vlc has the same issue, which leads me to believe it's a problem with the imported file, not strictly with mythtv.  Is there some way to correct this?

---

### Post by klc5555 on 2010-06-26
Traditionally, mythtv's ripper has had frequent difficulty in building a proper frame index while it rips. Third-party rippers, of course, don't build a frame index at all.

This is usually fixed after-the-fact by building (rebuilding) the frame index (seek table). Either with mythtranscode (which I prefer, because it was always a lot better with various mpeg 3rd-party rips and dvb files than mythcommflag ) or mythcommflag (which is generally the preferred tool nowadays).

mythtranscode --mpeg2 --buildindex --video -i [filename]

mythcommflag --rebuild --video [filename]

Check the specs for either utility at [http://www.mythtv.org/wiki/Mythcommflag](http://www.mythtv.org/wiki/Mythcommflag)

or [http://www.mythtv.org/wiki/Mythtranscode](http://www.mythtv.org/wiki/Mythtranscode)

---

### Post by zapstrap on 2010-06-26
That helps a lot, thanks.  I'm curious though, rebuilding the seek table for myth does not fix the problem in vlc.  Clearly the vob file is not being modified.  Why does the time display incorrectly in other applications? It seems like nothing over one hour displays correctly.

---

### Post by klc5555 on 2010-06-26
Can't help you there; I'm not sure how the 3rd-party players estimate playing time. I do notice that the estimated playing time given by Xine, and VLC do tend to be off by a fair amount. But if your rip of a known two-hour movie shows a playing time of, say, 1 hour and 5 minutes in Myth, it's probably that Myth's ripper has built you a bad frame index.

---

