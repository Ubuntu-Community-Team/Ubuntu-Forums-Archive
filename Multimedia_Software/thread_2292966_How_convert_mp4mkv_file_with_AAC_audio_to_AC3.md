---
title: "How convert mp4/mkv file with AAC audio to AC3?"
date: 2015-09-01
forum: Multimedia Software
---

### Post by jfca283 on 2015-09-01
Hi
Some time ago i used a script to perform that task.
It didn't touch the video. It just changed the audio format. From AAC to AC3.
Now i'm watching MKV/MP4 files which have the audio in the AAC format. Format that my receiver doesn't decode.
So, what can i do?
Where do i find an updated version of the old AAC2AC3 script?
Thanks for your time and interest.

---

### Post by shantiq on 2015-09-01
jf do this with your mkv

```
 time ffmpeg -i inputvideowithaacaudio.mkv -c:v copy -c:a ac3  outputmkvwithac3audio.mkv
```

replace ffmpeg with avconv if you have not got ffmpeg

---

### Post by jfca283 on 2015-09-01
The command you provide doesn't process the video, right?
The following line, should it work? 
time ffmpeg -i inputvideowithaacaudio.mp4 -c:v copy -c:a ac3  outputmkvwithac3audio.mkv 
Processing a mp4 file?

---

### Post by SeijiSensei on 2015-09-01
The command will copy the video stream and convert the audio stream and store the result in the Matroska container.

You don't need the "time" command at the beginning either.  That just tells the OS to report how long the task took.  ffmpeg will report that itself anyway.

---

### Post by jfca283 on 2015-09-01
So, for mkv files with AAC audio, i just need to run this
time ffmpeg -i inputvideowithaacaudio.mkv -c:v copy -c:a ac3  outputmkvwithac3audio.mkv
And for mp4, the following
time ffmpeg -i inputvideowithaacaudio.mp4 -c:v copy -c:a ac3  outputmkvwithac3audio.mkv
Am i right?

---

### Post by shantiq on 2015-09-01
yes you are right ¡totalmente!    the time thing is good to see how long it takes
good luck should be quick!


but your second line should read

```
 time ffmpeg -i inputvideowithaacaudio.mp4 -c:v copy -c:a ac3  outputvideowithac3audio.**mp4**
```

since you are keeping the same video -c:v copy = codec video copy  is what this means

---

### Post by jfca283 on 2015-09-01
Thanks!

---

### Post by Yellow Pasque on 2015-09-01
> but your second line should read ... mp4
ffmpeg would still copy the video and encode audio to AC3. It would then mux them into a Matroska container (instead of MPEG4 container). 
So it probably doesn't matter, unless the OP intends to play the video on a device/system that can't handle a Matroska container. I guess there could be some differences in the container (chapter markers, tag information), but ffmpeg is usually smart enough to copy those things from one container to another.

---

