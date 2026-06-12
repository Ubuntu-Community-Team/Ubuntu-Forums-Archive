---
title: "converting .mov to .flv"
date: 2013-02-16
forum: Multimedia Software
---

### Post by jamesbon on 2013-02-16
I have a digital camera which records videos in .MOV format, these videos a 15 minuted video is recorded in 1 GB size, I have lots of such videos, I am having lack of disk space on my machine.

So I decided to convert them to .flv, but I am not sure as how to convert .mov files to .flv can any one let me know how to do so?

I use Ubuntu 12.04 64 bit.

Also I want to know if there is a better solution for the problem I described?

---

### Post by andrew.46 on 2013-02-17
Rather than convert them, and I am not sure that .flv would be such a good choice, perhaps simply buy a big external drive and store the video files there...

---

### Post by Yellow Pasque on 2013-02-17
WinFF might make it easy.

---

### Post by sudodus on 2013-02-17
I use a script file running ffmpeg to make mp4 files encoded with the x264 codec
```
-vcodec libx264
```
But it is not in a brand new version of Ubuntu, so I don't know if it is available for you.

A simpler alternative is the default mp4 codec, which I think creates ***bigger*** files than x264, but faster (easier) to decode for the same resolution. I don't know how much smaller they will be compared to your original mov files, but sometimes camera files are poorly compressed.

Remember that is a good idea to keep the quality, so don't compress the files sacrificing the quality, because as was pointed out by andrew.46, you can get a big external drive for a reasonably price and store them there.

The reason I compress my files is to make them small and easy enough to play on aging hardware or to upload to some cloud service.

---

### Post by coldraven on 2013-02-17
I have not tried it but Handbrake will transcode .mov files.
Try making a .mp4 and see what it looks like.

---

### Post by mike acker on 2013-02-17
try avidemux

assemble movie a meg-4 AVC and 
 audio as MP3
 store in AVI container

---

### Post by evilsoup on 2013-02-17
I would second the recommendation of HandBrake, h.264 video+AAC audio in an MP4 is the current standard for video files.

---

