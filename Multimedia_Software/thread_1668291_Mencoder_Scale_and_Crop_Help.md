---
title: "Mencoder Scale and Crop Help"
date: 2011-01-16
forum: Multimedia Software
---

### Post by M4ttyB on 2011-01-16
Hi all, I have an avi file that I want to scale and crop. I do not want to change the video format or the audio format. I know how to copy audio or video using -oac copy and -ovc copy but Is it possible to copy both audio and video whilst performing Crop and Scale??????

I have tried this:

mencoder -ovc copy -oac copy -vf crop=720:384:00:96,scale=720:384 -o /path/to/output.avi /path/to/input.avi

It processes the file amd outputs an avi but no cropping or scaling has been done.

Thanks for your input......

M4ttyB

---

### Post by SeijiSensei on 2011-01-16
I think '-ovc copy' is incompatible with scaling because it doesn't alter the video stream.  You'll need to re-encode the video with something like '-ovc lavc' or maybe '-ovc xvid'.  See the [mencoder manual](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html) for details.

---

### Post by M4ttyB on 2011-01-17
Thanks for the reply.

I know how to re-encode the file, however I was hoping to possibly save some time in not having to re-encode it. The format of the file is OK.
If I re-encode the file to the same video bitrate using crop and scale and then copy the audio, will mencoder actually re-encode or is it smart enough to realise the bitrate is the same?
Seems like a lot of time wasting.......

Cheers M4ttyB

---

### Post by Prescilla on 2011-12-11
I've been trying to understand how to use the crop, scale and expand options of MEncoder, until now I haven't quite get it yet. So if anyone here could explain to me how to use these options, I would really appreciate it. I am trying to scale down a video without stretching it and I need to understand how to use these options.

Source video file is 1280x688 and I need to scale it down to 720x576. Need help. Thanks in advance.

---

