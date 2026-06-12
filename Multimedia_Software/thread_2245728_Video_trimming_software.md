---
title: "Video trimming software"
date: 2014-09-25
forum: Multimedia Software
---

### Post by timswait on 2014-09-25
Can anyone recommend a quick and easy application to trim video clips without any messing about rendering or transcoding? I've got a load of video clips from an action camera (hang gliding!) but on each clip there's a few minutes of messing about at the beginning and end of the clip that I'd like to get rid of. I can't find a quick and easy way to just trim these few minutes off. I've used OpenShot, which is very good for proper video editing, but it's time-consuming for doing what should be a simple job. The exporting of the video takes ages as it has to re-render 40 minutes or so of HD video, and I'm never sure if I'm exporting in exactly the same form that I'm importing. There must be some program that'll just cut the videos down without any re-rendering or complexity surely? I've had a look through the Software Centre but can't find anything that sounds like it'll do what I want. Any suggestions?

---

### Post by kostkon on 2014-09-25
avidemux

---

### Post by Rob Sayer on 2014-09-26
It's hard to recommend anything without knowing what video formats you're talking about.  For example, avidemux is very good with mpeg4 ASP or mpeg4 Visual.  Less so with h.264.  

If you don't know which format you're exporting to you need to RTFM.  A quick search found this:

[http://www.openshotusers.com/help/1.3/en/ar01s23.html](http://www.openshotusers.com/help/1.3/en/ar01s23.html)

The format may not be the problem anyway.  It's impossible for any editor to export without re encoding if you aren't cutting on key frames.  That's the nature of video compression.

---

### Post by FakeOutdoorsman on 2014-09-26
You can stream copy (re-mux) with ffmpeg. [Download a build](http://johnvansickle.com/ffmpeg/) and see [Seeking and Trimming with FFmpeg](https://trac.ffmpeg.org/wiki/Seeking%20with%20FFmpeg).

---

### Post by timswait on 2014-09-27
They're h.264 .MOV files. I'm quite happy to trim it on the nearest key frames, I simply want to delete about 5 minutes off the start of each file and 2 or 3 minutes off the end of the files and not to change anything else.

---

### Post by Rob Sayer on 2014-09-27
I don't use avidemux in linux for h.264.  The version in the ubuntu repos doesn't support it very well and I don't want to fart around with their dailies.

Try openshot.  It's a good combination of power and ease of use.

---

### Post by MartyBuntu on 2014-09-28
> **Rob Sayer said:**
> 

Try openshot.  It's a good combination of power and ease of use.

The OP stated they do NOT want to transcode.

---

### Post by Rob Sayer on 2014-09-28
> **MartyBuntu said:**
> The OP stated they do NOT want to transcode.

There aren't any issues with that program and h.264 I'm aware of.  It handles formats that even avidemux chokes on.

---

### Post by mc4man on 2014-09-28
I would just check/read  the link(s) in post 4 & use that, should be just fine
(do a test edit  & test in your player(s)
2 basic commands (either of these should work in ffmpeg or avconv, ffpmeg preferred, will produce slightly different files 

ffmpeg -ss [start pos] -i /path/to/whatever.mov -c copy -t [duration] edited.mov
ffmpeg -i /path/to/whatever.mov  -c copy  -ss [start pos] -t [duration] edited.mov

or with ffmpeg (recent) you can use -to 
ffmpeg -i /path/to/whatever.mov  -c copy  -ss [start pos] -to [end pos] edited.mov

---

