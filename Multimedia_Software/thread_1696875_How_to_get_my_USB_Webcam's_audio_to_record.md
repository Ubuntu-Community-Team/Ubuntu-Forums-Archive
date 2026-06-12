---
title: "How to get my USB Webcam's audio to record"
date: 2011-02-28
forum: Multimedia Software
---

### Post by nslegacy163 on 2011-02-28
I have read up [here]("http://ubuntuforums.org/showthread.php?t=385739&referrerid=1246731") on how to capture audio. I can see the green bar move up and down as the mic on my Logitech 9000 webcam picks up my voice. I can see myself as well using VLC and cheese. I stopped using cheese because it would freeze up on me. Regardless, VLC captures the video flawlessly. I have successfully recorded video. 

When I type ls /dev/audio* in terminal I return ls: cannot access /dev/audio*: No such file or directory. ls /dev/video returns /dev/video0 which is my logitech cam. 

I can also record video AND audio on youtube.com using their web based upload.

 So I know the mic works, and the sound application recognizes the mic from the webcam and youtube.com picks it up...so how do I get VLC to record it and/or audio* to list it? 

 Thanks!

---

### Post by tigeraway on 2011-05-20
I have exactly the same issue with my webcam - is there anyone who can point us in the right direction with this? Thanks.

---

### Post by nslegacy163 on 2011-05-20
> **tigeraway said:**
> I have exactly the same issue with my webcam - is there anyone who can point us in the right direction with this? Thanks.

 I went to System/Preferences/Sound looked like my mic kept getting muted by default. So that fixed it for me.

---

