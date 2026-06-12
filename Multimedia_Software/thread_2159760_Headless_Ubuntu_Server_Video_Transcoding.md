---
title: "Headless Ubuntu Server Video Transcoding"
date: 2013-07-04
forum: Multimedia Software
---

### Post by frotzed on 2013-07-04
So I have a question, but first I'll explain my setup.  I'm running Ubuntu server 12.04 headless on a decent PC.  Core2Duo processor, 2GB RAM, RAID 1 drives.  It's currently serving as a file server via Seafile and a media server via Plex and Subsonic for video and music, respectively.  I have an Alienware PC with a high-end graphics card that I'd like to convert into my server but I have a question.  

If I'm running Ubuntu server in a headless state, will the OS utilize the GPU on the discrete graphics card for video transcoding or will it only use the CPU?

** Edit: I went to the IRC channel and got my answer.  The answer is that the GPU is exposed to the OS, so if the software in question was designed to use the GPU then it technically could.  This is a question to the software developers more than the OS devs.  Thanks to fewt on the IRC channel.

---

### Post by dannyboy79 on 2013-07-05
what are you using the transcode? you could always go to that specific IRC channel

---

### Post by frotzed on 2013-07-05
That's exactly what I did.  I'm using PLEX to transcode.  I went to their forums and asked the question there.  Turns out PLEX will not use the GPU for transcoding, it relies solely upon the CPU.

---

