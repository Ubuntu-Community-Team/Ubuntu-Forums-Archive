---
title: "Video Editor Insert MP3"
date: 2009-06-07
forum: Multimedia Software
---

### Post by RealG187 on 2009-06-07
I am trying to upload a song to youtube for the first time and need an program that will let me make a slide show or show the same image and insert and MP3 file for the audio. I tried doing this in Avidemux and I get random errors.

Is there a program that does what I want?

---

### Post by RealG187 on 2009-06-07
I tried converting to WAV and OGG and tried using a different program and nothing works. wtf I know this is possible.

---

### Post by scragar on 2009-06-07
```
mencoder -o **OUTPUT.avi** -ovc copy -audiofile **AUDIO.mp3** -oac pcm **INPUT.avi**
```
Will add the AUDIO.mp3 soundtrack to the INPUT.avi video and save it as OUTPUT.avi

Use lame to convert to MP3 and mencode to encove your video as avi.

EDIT: I'm not sure how to get the video to the right length, or what happens if the length isn't enough, so some experimenting will be needed.

---

### Post by RealG187 on 2009-06-07
i have an mp3 and a picture

---

### Post by scragar on 2009-06-07
```
ffmpeg -t **N** -i **test.jpg** -y -an **out.avi**
```
That will convert a jpg image(or most other image formats as well, actually) to the video out.avi lasting N time(format hh:mm:s).

Also note that the default quality might not be that high, use
```
-s **X**x**Y**
```To change the resolution to X by Y

---

### Post by RealG187 on 2009-06-07
I tried and the length of the video was 0 seconds

---

