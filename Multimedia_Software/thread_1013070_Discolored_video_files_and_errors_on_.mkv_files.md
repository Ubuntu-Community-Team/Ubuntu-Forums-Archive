---
title: "Discolored video files and errors on .mkv files"
date: 2008-12-16
forum: Multimedia Software
---

### Post by rv65 on 2008-12-16
Basically all my videos that have are being discolored by any video player. For some reason it started doing that. It was fine before but now it just happened. I've tried to install and reboot a few times and nothing works. Now a few of my video programs like realplayer and totem now have errors on .mkv files. I'm sure they're normal but all of my video programs are doing this. Any help would be great.

---

### Post by rv65 on 2008-12-16
MKV files now work but all the skin tones are blue and the color hues are terrible. Flash video works fine but not regular video.

---

### Post by rv65 on 2008-12-16
Well I solved my problem by typing gstreamer-properties and fixed it.

---

### Post by rv65 on 2008-12-16
I though it work but it now doesn't. 

```
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(463): gst_v4l2_open (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src4:
system error: No such file or directory]

```

This is what it says. Anything wrong. It now discolors again. I'm still trying to find out whats wrong.

---

### Post by rv65 on 2009-01-24
Now it just started discoloring video. There must be something wrong with gstreamer or something like that. All players will discolor video with some bluish tint. I had it working but now it's just doing that so any ideas.

---

### Post by gabbah on 2009-11-18
I have the exact same problem.
I'm watching videos as usual, and then suddenly when i start to play a new video, the color is tinted, for all subsequent videos, for all videoplayers. When I restart X (log out, log in), the color in video playback is back to normal, until some video does the same again... And the thing is, it's not always the same video, so it may not be something wrong with the video file. That is, after a restart of X, playing back the SAME video file will not result in tinted color again.
The problem is not just on mkv files for me.

For me the problem started after upgrade to Ubuntu 9.10.

---

### Post by harmck on 2009-11-19
Hi, 

I have the same problem since my upgrade to 9.10, does anyone if a bug has been logged in relation to this? Again, my occurs with any video file and after I reboot or log back in it resolves. 

Any advice on the problem would be welcome.

Rgds, 
Har

---

### Post by bung_shwey on 2009-11-22
Same problem after upgrade to karmic...

---

### Post by Spectre5 on 2009-11-22
Try this:

"Click on: Application -> Sound & Video -> Movie Player
The click on: Edit -> Preferences -> Display -> Reset To Defaults"
Post #7 by Stéphane at [http://ubuntuforums.org/showthread.php?t=1158246](http://ubuntuforums.org/showthread.php?t=1158246)

---

### Post by ricardisimo on 2009-11-28
> **Spectre5 said:**
> Try this:

"Click on: Application -> Sound & Video -> Movie Player
The click on: Edit -> Preferences -> Display -> Reset To Defaults"
Post #7 by Stéphane at [http://ubuntuforums.org/showthread.php?t=1158246](http://ubuntuforums.org/showthread.php?t=1158246)

Thank you so much, Spectre5. That seems to have fixed the problem on all of my players (which is weird, but I'm not complaining.)

Can someone explain how this became a problem in the first place?

---

