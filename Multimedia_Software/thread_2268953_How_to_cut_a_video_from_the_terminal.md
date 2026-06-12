---
title: "How to cut a video from the terminal?"
date: 2015-03-12
forum: Multimedia Software
---

### Post by remmas-sido on 2015-03-12
Hello guys 
I would like to know the method used to cit a video in the terminal, I have one in MP4 format and the other in MKV, and is there anyway besides the terminal my goal is to cut a specific scene.

---

### Post by deadflowr on 2015-03-12
moved to multimedia

---

### Post by papibe on 2015-03-12
Hi remmas-sido.

You can do that with avconv or ffmpeg. Take a look at this [example]("http://askubuntu.com/questions/56022/what-to-use-to-quickly-cut-audio-video").

Let us know if that helped, or if you need more questions.
Regards.

---

### Post by TheFu on 2015-03-12
mencoder will let you cut parts too, nothing against ffmpeg or avconv. All will work with about the same level of difficulty and resulting output.

BTW - mp4 and mkv are just containers. The codecs used for video and audio will matter.  Frame accurate cuts generally aren't possible.
If you need a GUI, avidemux is pretty easy.

---

