---
title: "no sound in mkv files with xine-ui"
date: 2008-02-22
forum: Multimedia &amp; Video
---

### Post by yorick on 2008-02-22
Hello.

Since 2 or 3 days ago when there was an update to ffmpeg libraries (if I remember correctly) I can hear no sound in mkv files played with xine-ui.

Does anyone else have have this problem or a solution?

---

### Post by yabbadabbadont on 2008-02-22
Is it all mkv files, or just the ones with ogg-vorbis sound?  Seems to me, I read about a xine issue with ogg-vorbis audio in mkv files.  I didn't read any solutions though.  But if that does match your issue, then at least you now have some more information with which to search for a solution.

---

### Post by yorick on 2008-02-22
I am not sure. I am at work right now and I can't check. But I will look into it this evening.

Thanks for the hint.

---

### Post by yorick on 2008-02-24
I can confirm that this issue happens only with mkv files with ogg-vorbis audio.

The libxine version 1.1.10 from gutsy-backports has this problem. I tried downgrading to version 1.1.7 from gutsy but didn't succeed. 

I guess I'll have to play these files with mplayer until the problem is resolved.

---

### Post by Awperator on 2008-05-23
> **yorick said:**
> I can confirm that this issue happens only with mkv files with ogg-vorbis audio.

The libxine version 1.1.10 from gutsy-backports has this problem. I tried downgrading to version 1.1.7 from gutsy but didn't succeed. 

I guess I'll have to play these files with mplayer until the problem is resolved.

Is there anywhere that I can find out more information about Xine's inability to play audio from video files with Vorbis encoding? Is it being worked on? I am still having issues with Xine and vorbis.

---

