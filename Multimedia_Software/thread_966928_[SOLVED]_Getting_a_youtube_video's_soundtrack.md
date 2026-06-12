---
title: "[SOLVED] Getting a youtube video's soundtrack"
date: 2008-11-01
forum: Multimedia Software
---

### Post by crazyfuturamanoob on 2008-11-01
I want to get a soundtrack of a youtube video.

For first, I tried youtube-dl. It downloaded video but no sound at all.

Then, I tried to record from soundcard's output directly, when playing the video, with KRec. Didn't work, it recorded nothing, no matter of settings.

And finally, I tried getting the .swf file itself from youtube, and using swfextract to get the soundtrack out of the file, but I couldn't figure a way to download the swf file.
I actually downloaded some swf files, but they were invalid, or didn't contain the video.

Anybody got an idea how to accomplish this task?

Edit: Managed to download the video with clive. Now I got it in a single .flv file, including audio. Converted to avi with ffmpeg. How to extract sound track from avi?

---

### Post by ajtaggs on 2008-11-01
You can use audicity (open source sound editing) and record it off of the audio out. I have done this before.

---

### Post by tomkinsc on 2008-11-01
You might try using a web service. A quick Google search pointed me [here]("http://vixy.net/").

---

### Post by FakeOutdoorsman on 2008-11-01
The [youtube-dl]("http://www.arrakis.es/~rggi3/youtube-dl/") script should have worked.  Did you try the latest version?  Use ffmpeg to get the audio.  You can copy the audio stream instead of re-encoding.  This preserves the quality:
```
ffmpeg -i input.flv -acodec copy output.mp3
```

---

