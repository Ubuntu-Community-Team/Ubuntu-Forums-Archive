---
title: "FFmpeg/mencoder merge audio file"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by jjhoal on 2008-03-31
Hi, I am new to this forum and I might need your help.

I guess I have seen a multiple post around here about mencoder and ffmpeg and Im looking if someone knows how to merge two audio files using neither of the two application. 

I have used mencoder to merge two video files to one video, but when I try to merge the audio files (concatenate) it wont work properly. Any idea on how to do this ? 

I have this code that works on merging video. But it wont work on audios:

mencoder -oac copy -ovc copy -o "joined.mpeg" "movie1.mpeg" "movie2.mpeg"

I hope someone might know the answer to this questions. 

Thanks and my regards.

---

### Post by warp99 on 2008-03-31
The string should be:

```
mencoder -oac copy -o joined.mpeg movie1.mpeg movie2.mpeg
```

No video, no need to use the -ovc parameter. Since there mpg you should just be able to cat the files.

```
cat movie1.mpeg movie2.mpeg > joined.mpeg
```

Hope this helps.

---

### Post by jjhoal on 2008-04-02
Hi thanks for your help. :D 

Anyway, is it also possible to cat two audio files, yet they will play at the same time? like overlaying audio1.mp3 to audio2.mp3 resulting to one file which two audios will play at the same time at the very beginning?

---

### Post by warp99 on 2008-04-02
> **jjhoal said:**
> Hi thanks for your help. :D 

Anyway, is it also possible to cat two audio files, yet they will play at the same time? like overlaying audio1.mp3 to audio2.mp3 resulting to one file which two audios will play at the same time at the very beginning?

AFAIK you can't do that with the cat, mencoder or ffmpeg commands. You need a sound editor that can handle multiple inputs. Check in the Ubuntu: Multimedia Production section of the forums for some ideas on a good program to do that.

---

