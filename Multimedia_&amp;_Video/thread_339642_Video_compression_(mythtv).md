---
title: "Video compression (mythtv?)"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by sfpiano on 2007-01-16
I just got my first recording and for a 30 min video the file size turned out to be 1.1Gb, which seems enormous to me. My main question is what can I use to compress the video down, and my other questions is if anyone knows if there is some option to set compression in mythtv itself.

---

### Post by deadgobby on 2007-01-16
You could try using Kino to see if you can get is snub down. the only other way is like making into a compress file like Zip
[https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

---

### Post by majoridiot on 2007-01-16
you can set mythtv to automatically transcode to high, medium or low quality, choose codec, 
etc. (and edit commercials too)... most of the settings are in the frontend setup, but you may
need to check the jobs settings on the backend too.

---

### Post by wilderness wanderer on 2007-01-17
In addition to the transcoding settings, you can adjust the resolution and bitrate that you are recording at.  If you have a hardware encoder card (Hauppauge PVR-150/250/350/500) you should probably stick to MPEG-2 to take advantage of the hardware acceleration.  However, you can adjust the resolution and bitrate.  The default bitrate for MPEG-2 is I believe 4.5Mbps with a max of 6MBps.  This produces very large files, but if you have the space and are going to delete them in a few days after watching them-- don't worry about it.  If you lower the bitrate you will get to the point where the quality is noticeably worse, and this will happen much faster if you are watching on a monitor as opposed to a TV.  

You also have the option of using software encoding.  If your CPU is fast enough, you can encode directly to MPEG-4.  The settings for this are adjustable too.  All of this is in the recording profiles under TV settings from the frontend.

---

