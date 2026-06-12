---
title: "ffmpeg audio sync"
date: 2010-07-09
forum: Multimedia Software
---

### Post by Nonno Bassotto on 2010-07-09
I have a file where the audio is out of sync in the second part. It also needs to be cropped, but that is a plus.

I know I can crop a video by something like
```

ffmpeg -i In_Movie.avi -croptop 74 -cropbottom 74 -sameq -aspect 16:9 Out_Movie.avi

```
but I don't know how to shift audio, let alone shift only a part of it.

Can any ffmpeg expert help me complete the command?

---

### Post by andrewthomas on 2010-07-10
> **Nonno Bassotto said:**
> I have a file where the audio is out of sync in the second part.  I don't know how to shift audio, let alone shift only a part of it.

Can any ffmpeg expert help me complete the command?
I can help with a bit, but am also looking for some answers.  I was having a similar problem and I used avidemux to split the video into parts where the video is synced differently.  Checking the shift box and testing out different rates I was able to get all the parts in sync.  Then, I just used file>append to add all the bits back together.  Now the file is in sync when I play it in avidemux, yet it still in not in sync when played in totem or vlc.
Hopefully, someone with a bit more editing experience can jump in and provide a complete solution.

---

### Post by Nonno Bassotto on 2010-07-10
Thank you very much for your suggestion. Still I'd need something which works in common media players. I'm quite sure some encoders are able to do this, but I don't know how.

By the way, did something change in Totem and VLC? I mean, the audio is still not in sync, but did the delay change or it is still the same?

---

### Post by andrewthomas on 2010-07-14
I pretty much figured it out.  Check it out in this thread. [http://ubuntuforums.org/showthread.php?t=1529640](http://ubuntuforums.org/showthread.php?t=1529640)

---

### Post by Nonno Bassotto on 2010-07-14
Thank you very much! I will try to do it as you suggest.

---

### Post by andrewthomas on 2010-07-14
You are welcome.  It took a bit of work, but I have now burnt a DVD out of the file and the audio and video are properly synchronised throughout.  Let me know how you came out.

---

