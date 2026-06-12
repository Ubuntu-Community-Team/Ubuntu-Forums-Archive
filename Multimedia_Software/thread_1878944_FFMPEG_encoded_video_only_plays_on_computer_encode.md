---
title: "FFMPEG encoded video only plays on computer encoded on"
date: 2011-11-10
forum: Multimedia Software
---

### Post by brianatlarge on 2011-11-10
So I'm encoding video that's coming off a tuner card using this command:

```
ffmpeg -i /dev/video0 -vcodec libx264 -vpre medium -threads 0 -crf 30 -deinterlace -t 60 test.mp4
```I can play this video fine on the computer it's being encoded on, but if I try to play it back on any other computer (Windows or Mac), I can't get it to play. I've tried Windows Media Player, Quicktime, and VLC.

What am I doing wrong?

---

### Post by brianatlarge on 2011-11-11
So a little test.

I tried encoding the captured video using the same settings as before. So basically I'm encoding the captured video twice. If I do this then I can view the encoded video anywhere. 

```

ffmpeg -i /dev/video0 -vcodec libx264 -vpre medium -threads 0 -crf 30 -deinterlace -t 60 test.mp4
ffmpeg -i test.mp4 -vcodec libx264 -vpre medium -threads 0 -crf 30 test2.mp4

```

But I only want to have to encode the video once. What's the deal with encoding a streaming source and encoding a regular file? Shouldn't both output a file that can be viewed anywhere?

---

### Post by BicyclerBoy on 2011-11-11
Just a guess but..
It could be the moov atom (location in file).

A recorded stream can not have the moov atom at the beginning because the file size etc is undefined..
This is why transport stream containers exist.

A streamed file can not be played (while streaming) unless the moov atom is at the beginning..

You may be able to fix with  qt-faststart or use -vcodec copy.
I'm sure you'll get an informed answer before long..

---

### Post by brianatlarge on 2011-11-11
Well... nevermind. Turns out when I was FTPing the video, it was sending using ASCII mode instead of binary, so FFMPEG had absolutely nothing to do with it.

---

