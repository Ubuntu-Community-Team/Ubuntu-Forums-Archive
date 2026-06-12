---
title: "Converted MP3 to MP4 will not process on YouTube"
date: 2020-02-13
forum: Multimedia Software
---

### Post by robertcull1 on 2020-02-13
I two MP3s. One I created with Audacity. Another is a downloaded MP3 music recording.


I have tried various ways to convert the MP3s to MP4s. I have used ffmpeg with the command:


```
ffmpeg -i /home/robert/Music/hymn.mp3 -shortest -b 1000k -acodec copy /home/robert/Music/hymn_ffmpeg.mp4



```I have also tried converting with VLC using all these profiles.


Video - H.264 + MP3 (MP4)
Video - VP80 + Vorbis (Webm)
Video - H.264 + MP3 (TS)
Video - H.265 + MP3 (MP4)
Video - Theora + Vorbis (OGG)
Video - MPEG-2 + MPGA (TS)
Video - Dirac + MP3 (TS)
Video - WMV + WMA (ASF)
Video - DIV3 + MP3 (ASF)
Video for MPEG4 720p TV/device
Video for MPEG4 1080p TV/device
Video for DivX compatible player
Video for iPod SD
Video for iPod HD/iPhone/PSP
Video for Android SD Low
Video for Android SD High
Video for Android HD
Video for Youtube SD
Video for Youtube HD


I can successfully upload these MP4s but after the file is uploaded and it tries to process the files I get a red "processing abandoned" message.


Are there any other ways to convert an MP3 into an MP4 that I have overlooked?


I have tried many google searches for "processing abandoned youtube upload" and I can't find any relevant webpages.


Please help.

---

### Post by TheFu on 2020-02-13
mp3 is an audio format.

mp4 is a video container.   That means some sort of video has to be included with the specific, allowed, supported, converted, audio that an mp4 container supports.

I don't know the answer, but if I were trying to do this, then I'd download a working mp4 container from the service, look at the audio and video codecs used, then build my mp4 file to be the same.  If I didn't have a video to go with the audio file, I would learn how to use a single image to fit that need, similar to the way that audio podcasts and audiobooks do it.

Google " adding image to audio file mp4" - 73,000,000 results for that.  Here's 1 [https://superuser.com/questions/1041816/combine-one-image-one-audio-file-to-make-one-video-using-ffmpeg](https://superuser.com/questions/1041816/combine-one-image-one-audio-file-to-make-one-video-using-ffmpeg)

---

### Post by robertcull1 on 2020-02-14
Your link contained the answer. I used something like this:

```
ffmpeg -r 1 -loop 1 -i image.jpg -i input.mp3 acodec copy -r 1 -shortest -vf scale=1280:720 output.mp4
```

Thanks and best wishes.

---

