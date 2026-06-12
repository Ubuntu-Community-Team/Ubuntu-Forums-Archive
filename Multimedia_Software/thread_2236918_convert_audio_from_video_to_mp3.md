---
title: "convert audio from video to mp3"
date: 2014-07-29
forum: Multimedia Software
---

### Post by acefromspace on 2014-07-29
What is a simple way to get the audio from a video and convert it to mp3 ?

---

### Post by TheFu on 2014-07-29
ffmpeg?  What have you tried so far?

---

### Post by ajgreeny on 2014-07-29
A video file or is it a DVD?  You can open many video files in audacity (it will only play the audio from the file) and you can then export the audio to an mp3 as long as you have the correct codecs for encoding mp3.

In the command line you can also use avconv with, for example ```
avconv -i file.mp4 -acodec libmp3lame -ab 128k file.mp3
```

---

### Post by acefromspace on 2014-07-30
Video files are mp4. I seem to remember using avidemux and choosing save audio, then converting to mp3, but I never really understood how to use avidemux... any good tutorials for this? I also have ffmpeg, but don't I need to extract the audio first?

---

### Post by TheFu on 2014-07-30
> **acefromspace said:**
>  I also have ffmpeg, but don't I need to extract the audio first?

No, you do not.  avconv and ffmpeg options match. Try the command above.
or this might work:

```
ffmpeg -i file.mp4  file.mp3
```

---

### Post by erhollowell on 2014-08-09
My advice, open in audacity and export it as mp3. This also gives you a chance to add audio info and create tracks if that pleases you. Audacity does the conversion from MP4 to form that audacity can use automaticly. After you decide what you want it is only a matter of going to file menue and export or export selection. Tell it what you want to call it and what format you want and you will have it your way.

---

### Post by mn_voyageur on 2014-08-10
+1 for avconv

I used FFMPEG.  Now, I use avconv.

MarkN

---

### Post by FakeOutdoorsman on 2014-08-10
I use ffmpeg (the real one from FFmpeg), but not avconv. You still have a choice. [Download](https://ffmpeg.org/download.html) or [compile](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu).

Also see [FFmpeg MP3 Encoding Guide](http://trac.ffmpeg.org/wiki/Encode/MP3) (not guaranteed to work with avconv).

---

### Post by acefromspace on 2014-08-10
Audacity works great. Open file, export, choose mp3 and add info.

---

