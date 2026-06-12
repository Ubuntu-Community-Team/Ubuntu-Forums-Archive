---
title: "extracting, cleaning and re merging audio"
date: 2012-10-21
forum: Multimedia Software
---

### Post by marks_linux on 2012-10-21
I'm working on some videos with bad background noise. I'm using Openshot to edit the clips. I was hoping the audio track would be separate in the Openshot UI so I could extract it, clena it up in Audacity and then re-import.

Are there any tools that allow this to be done simply? I love commandline until I'm talking video, sound, codecs and bitrates!

thanks

---

### Post by shantiq on 2012-10-21
ok simple  [he says]




use ffmpeg to separate  audio and video   **first check properties of videofile see if your audio is aac   or mp3 **   and write in accordingly below


> ffmpeg   -i  audiovideo.mp4  -vn  -acodec copy  audio.**mp3**   && ffmpeg   -i  audiovideo.mp4  -an  -vcodec copy  videomute.mp4




you now have both separated and the original still


take audio mp3 to audacity and play around until happy:KS   save it as audio2.mp3







 reassemble with ffmpeg too   [ thank you FakeOutdoorsman !]

> ffmpeg -i videomute.mp4 -i audio2.mp3 -c copy newvideowithnewsound.mkv




**===================================**



or use   mencoder here   thus

> mencoder -ovc copy -audiofile audio2.mp3 -oac pcm   videomute.mp4 -o newfinal.mp4      but not as good as audio has to be hiked to pcm   better ffmpeg here   the whole way


or [FONT="Century Gothic"]**reassemble**[/FONT] in kdenlive  [in synaptic]

---

### Post by FakeOutdoorsman on 2012-10-21
> **shantiq said:**
> probably can reassemble with ffmpeg too  but not sure how  so please add anyone if you do

Assuming *video.mp4* has no audio streams. Newer syntax:
```
ffmpeg -i video.mp4 -i audio.mp3 -c copy output.mkv
```
Older syntax:
```
ffmpeg -i video.mp4 -i audio.mp3 -vcodec copy -acodec copy output.mkv
```

You can output to almost any container that supports your video and audio formats. If *video.mp4* has audio, and you only want the video from it while adding the audio from *audio.mp3*, then you will have to use the *-map* option. It is explained here: [FFmpeg mux video and audio from another video](http://stackoverflow.com/a/12943003/1109017).

---

### Post by shantiq on 2012-10-21
excellent Fake    thanx:KS   will edit previous post

---

### Post by marks_linux on 2012-10-21
Thanks guys, that seems pretty straight forward - once you are pointed the right way. I'll give it a shot this afternoon when back at the laptop.

---

