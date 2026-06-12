---
title: "Can't fast forward video after burning to DVD"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by 01steven on 2008-01-14
I burnt a DVD using Ubuntu's CD/DVD Creator application.
The original file was an avi video file (sorry don't have full technical specs of file to hand - think it was a divx or xvid file of sorts).
It burnt OK and played on another DVD player, but the video could only be paused, not fast forwarded or rewound.
Why was this?
Something to do with the codecs in the avi file?
How can I resolve this in future?

---

### Post by Keith_Beef on 2008-01-15
Not in my DVD player, but occasionally I've ripped a DVD to an AVI file, and mplayer and xine have been unable to fast forward. These have been single-pass rips using acid::rip as a front end to mencoder.

The programs complain, with a message along the lines of "cannot fast forward without an index".

 If I use a two-pass process, I don't have any problems.

I have also used mencoder to take an already ripped AVI file, and re-encode it in two passes, which seems to rebuild the index.

Beef.

---

