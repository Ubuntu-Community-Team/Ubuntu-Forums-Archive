---
title: "Cheese Recording - Audio lags Video too much!!"
date: 2009-03-05
forum: Multimedia Software
---

### Post by jiapei100 on 2009-03-05
I tried to use "cheese" to record a video for my application.

Cheese works perfect when recording, namely, voices (audio) and images (video) synchronized perfectly. You can't see and time lag between audio and video.

However, after finishing recording, the recorded video is automatically encoded and saved as a .ogv file. When this .ogv file is being play-backed, audio lags video quite a lot. 

So, anybody can tell me how .ogv file is encoded and how to avoid this asynchronism?

Rgds
JIA

---

### Post by jiapei100 on 2009-03-07
No idea whether 
cheese can deal with two audio channels or not.

In my case:


I've recorded a video by "cheese" which lasts around 3.9 seconds. I saved the video in default .ogv .

What I analyzed by ffmpeg and obtained the following info:

Video info: Width=640 Height=480 BitRate=2379 FrameRate=30
Audio info: SampleRate=44100 BitRate=80 Channels=1
Audio Signals 345216
Video Signals 119

Let's do a simple computation:

119/30 = around 3.9 seconds
345216/44100 = around 7.8 seconds

It seems there should be two audio channels, rather than one, but ffmpeg only detects one.

So, I doubt cheese has something wrong when recording the audio streams.

Please, do give me a reply!!!!

Cheers
JIA

---

### Post by hansdown on 2009-03-07
Hi jiapei100.

I've been looking at my cheese install, and have noticed that there aren't

many ways to change settings.

It may be that your distro, gutsy is doing the best it is able to.

Have you considered moving to a newer distro?

I have a link for their site, though it probably won't be of much help,

save for the required apps to go with it.

[http://projects.gnome.org/cheese/](http://projects.gnome.org/cheese/)

---

### Post by jiapei100 on 2009-03-08
Hi, sorry, I should have updated my info long time ago. 
Currently, I'm using Ubuntu 8.10 Intrepid. And, "cheese" version is
2.24.2, which is grabbed from Synaptic directly from Intrepid repository.

I think probably, "cheese" failed to codec audio with two channels.

The reason why audio lags video too much is because the VLC or other media players fail to detect it's two audio channel rather than just one.

This is very very very possible because I read the saved file from my own FFMPEG based code, and it shows the audio is only one channel. But, it's quite obvious that there are two audio channels if you use Audacity to verify this. And, that explains why in the saved file using cheese, audio lags video too much, say, roughly two times longer.

I'm not quite sure about it, but it is possible anyway.

Rgds
JIA


> **hansdown said:**
> Hi jiapei100.

I've been looking at my cheese install, and have noticed that there aren't

many ways to change settings.

It may be that your distro, gutsy is doing the best it is able to.

Have you considered moving to a newer distro?

I have a link for their site, though it probably won't be of much help,

save for the required apps to go with it.

[http://projects.gnome.org/cheese/](http://projects.gnome.org/cheese/)

---

### Post by hansdown on 2009-03-09
This may help.

[http://blog.mymediasystem.net/uncategorized/poor-mans-workaround-for-cheese-zero-byte-problem-on-ubuntu-810-intrepid-ibex/](http://blog.mymediasystem.net/uncategorized/poor-mans-workaround-for-cheese-zero-byte-problem-on-ubuntu-810-intrepid-ibex/)

Also here.

[http://www.google.ca/search?q=audio+in+cheese+in+ubuntu+8.10&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=audio+in+cheese+in+ubuntu+8.10&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

There seems to be a bug report for similar behavior.

---

### Post by jiapei100 on 2009-03-11
Thanks

Problem solved.

Most probably, it's due to my webcam is 
"08dd"


Now, I changed a UVC compatible one, everything synchronize perfectly. 

Best Regards

---

### Post by hansdown on 2009-03-12
Good work jiapei100.

---

