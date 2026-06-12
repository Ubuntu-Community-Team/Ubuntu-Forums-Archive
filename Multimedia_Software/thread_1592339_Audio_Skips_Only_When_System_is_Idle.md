---
title: "Audio Skips Only When System is Idle"
date: 2010-10-10
forum: Multimedia Software
---

### Post by atiek on 2010-10-10
Hello, I'm new to the Ubuntu forums.  I've been using Ubuntu for a while, but this is the first time I've had a problem that I'm not sure how to solve myself.

I had this problem in the previous release, but not in 9.10 (which I went back to).  I was hoping it would clear up in 10.10, but it hasn't.  Whenever I play a song in any program, or a video in any program, the audio/video will skip ONLY when I'm not moving my mouse or doing any other process.  If I constantly move my mouse around, the audio/video will not skip.  I was watching a video earlier while transferring a large amount of files in the background, and no skipping occurred.  It only happens when I'm not moving my mouse or doing anything else.

It doesn't seem like a pulseaudio or alsa problem.  I'm baffled as to why this happens, or how I can fix it.

Edit:
Solved this myself.

Installed the 64 bit version on a whim to see if that would help.  At first, the same problem persisted.  After googling a little more thoroughly, came across this site about disabling ipv6.

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

After following the directions there and rebooting, the problem went away.

I went ahead and tried it on the 32 bit version of 10.10 I originally installed, but disabling ipv6 did not solve the problem. Kinda strange.

---

