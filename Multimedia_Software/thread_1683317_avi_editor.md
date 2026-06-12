---
title: "avi editor"
date: 2011-02-07
forum: Multimedia Software
---

### Post by Tristan Tonks on 2011-02-07
Hi everyone,

I have an an .avi I created in Blender and a .wav file that I want to 'stitch' into it, I have tried all the most common suggestions to no avail.

Obviously Blender can edit the audio as can Kdenlive which is a great little program but I can find nothing (except excessively involving) programs that will do this?

Any ideas?

---

### Post by ridetheteapot on 2011-02-08
you can use mencoder like> mencoder -ovc copy video.avi -audiofile sound.mp3 -oac copy -o newvideo.avi
or to add a wav and encode it as mp3 into the video:
> mencoder video.avi -o newvideo.avi -ovc copy -oac mp3lame -audiofile sound.wav
or avidemux is a nice gui solution.

just made the same suggestion to someone else.

---

