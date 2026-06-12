---
title: "When sound at remote sink, flash doesn't work"
date: 2010-01-23
forum: Multimedia Software
---

### Post by ThomasNovin on 2010-01-23
Hello!

I just reported a bug to Launchpad ([#511562]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/511562"). 

I'm not sure if this bug is in flashplugin-installer or pulseaudio.

Problem:

When I use Firefox or Chrome for watching a flash video from Youtube for example, all works good. I then transfer the sound to a remote sink using Sound Preferences > Output > Internal Audio Analog Stereo on myuser@otherhost.

After this is done, the flash video halts. This is also true if I restart firefox and start a new video, already having transferred the sound. Sometimes you can see the video taking huge skips forward. For example, on a 3 minute music video, I see 3-4 different frames from different places in the video.

The sound is OK though!

100% reproducible and if I transfer the sound back to local speakers the video resumes and plays perfectly.

Has anyone else seen this?

---

### Post by ThomasNovin on 2010-02-03
Actually it seems transferring sound doesn't work good, period! 

If I just play a mp3 in Totem it plays nicely locally but when I transfer to a remote sink it sounds at the remote end but just for a few seconds, then stops.

---

