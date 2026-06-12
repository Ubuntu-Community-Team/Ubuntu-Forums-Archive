---
title: "FFmpeg streaming"
date: 2012-05-15
forum: Multimedia Software
---

### Post by breizh29 on 2012-05-15
Hi everybody,
 
In my project, I want to encode a video file in H.264 in a first computer, and stream the encoded video on a second computer to decode the stream.
 
I didn't find anything like this on internet. So, I would like to have some informations about that.
 
If it is possible or not ?
What is the syntax to encode and stream it ?
What is the syntax to decode the stream ?
And in practice, how to do that ? (I mean when start the encoding, the decoding, ...)
 
Thanks

---

### Post by Derek Karpinski on 2012-05-15
Either VLC for a GUI, or FFServer for command line only will handle this.

[http://ffmpeg.org/ffserver.html](http://ffmpeg.org/ffserver.html)

---

### Post by FakeOutdoorsman on 2012-05-15
> **breizh29 said:**
> In my project, I want to encode a video file in H.264 in a first computer, and stream the encoded video on a second computer to decode the stream.
The clarify, do you want to encode the video and then decode it on the other computer, or you do you want to encode the video and decode it as it is encoding? The first method is much easier.
 
> **breizh29 said:**
> If it is possible or not ?
Yes. Once method is to use *sshfs* to mount a remote directory. On the decoding computer:
```
mkdir remotevideo
sshfs user@192.168.1.155:/home/computer1/video removevideo
cd remotevideo
ffplay video.mp4

```

> **breizh29 said:**
> What is the syntax to encode and stream it ?
The syntax depends on your ffmpeg version which depends on your Ubuntu version. You didn't supply this information so I can't give an accurate example. You also did not mention any other specific information about what you need.

> **breizh29 said:**
> What is the syntax to decode the stream ?
Simply playing the file will decode it. Or you can benchmark decoding only with:
```
ffmpeg -benchmark -i INPUT -f null -
```
(Assuming ffmpeg from the repository has the null muxer.)

---

