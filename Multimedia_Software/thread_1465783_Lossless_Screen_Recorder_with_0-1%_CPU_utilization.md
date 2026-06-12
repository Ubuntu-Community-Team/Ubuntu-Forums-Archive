---
title: "Lossless Screen Recorder with 0-1% CPU utilization?"
date: 2010-04-29
forum: Multimedia Software
---

### Post by DodgeV83 on 2010-04-29
Does Ubuntu have a lossless screen recorder that uses extremely low CPU, and doesn't require me to "Compress video" immediately?

I've used Recordmydesktop, which works great in Zero Compression mode, but forces me to wait while the program compresses the video once I've stopped it.  For a 3 hour video, this could mean a 30+ minute wait, unfortunately I don't have that luxury.

I'd like the program to record the screen with Zero Compression, then give me the option to compress it later, preferably on a different computer.

[LIST]
[*]I've tried stopping the video, copying the tmp files somewhere else, then running the "recordmydesktop --rescue" option, but it always gives me a segmentation fault.  I've heard the idea of starting a new recording and copying the old tmp files there, but that's not scalable and doesn't always work.


[*]I've tried recording the screen using FFMPEG with "rawvideo" and PCM as the codecs, but the CPU utilization is too much.


[*]I've tried Recordmydesktop in Encode-On-The-Fly mode, but CPU utilization is too much (12%).


[*]I've tried the Istanbul recorder, but the CPU utilization is too much and the program constantly crashes.


[*]I've tried VLC screen recording (didn't know that as an option!), too much CPU.


[*]I've tried XVidScreenCap and the CPU was 130% somehow.


[*]I've tried RecordItNow, but it just uses Recordmydesktop on the backend.


[*]I've tried recording a local VNC session with pyvnc2swf, but it doesn't capture audio and used too much CPU.


[/LIST]
Nothing works.  Is what I'm looking for possible?  A program that simply looks at the input and saves it off without compression allowing me to compress it later?

---

