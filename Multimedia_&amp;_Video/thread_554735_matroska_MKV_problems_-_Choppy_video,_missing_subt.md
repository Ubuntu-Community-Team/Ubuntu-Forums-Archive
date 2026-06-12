---
title: "matroska MKV problems - Choppy video, missing subtitles in Kaffine."
date: 2007-09-19
forum: Multimedia &amp; Video
---

### Post by Ellipsys on 2007-09-19
Hello all. I'm currently running Kubuntu Fiesty, and am having difficulties with the following.

1. Matroska files in Kaffine seem to have choppy video. The audio is fine, but the video is choppy and seems to have a difficult time rendering. 

2. Matroska files that have subtitles seem to be disabled or just plain won't show up? 

3. For some reason, video files played from over a network drive, hang after about 1 second of playtime. In the event I copy and paste the file to my HDD, it plays "fine" (that is to say, still having issues listed above if its MKV).


I have W32codecs and such, but I'm just not sure what the issue is here. Any suggestions? Thanks!

---

### Post by shirilover on 2007-09-19
A few things to determine the exact problem.

1) What is the resolution and video codec used in these particular mkv files?
Large resolution H.264 video requires significant processing power to play smoothly.

2) Are the subtitles soft-subs(selectable on/off) or are they actually encoded in the video stream?
Soft-subs are generally not set to be shown as default, you will need to actually select to have them be shown. As I do not use Kaffiene, I cannot tell you how this can be accomplished.

---

### Post by RomeReactor on 2007-09-19
Hi. As **shirilover** said, if the files are encoded in h264, that would probably explain the choppiness; I don't have Kaffeine installed, so I can't assure you that it won't play them correctly, but for me Totem drops a lot of frames with h264 MKV files. Try opening them with Mplayer; it might play them correctly for you, as it does here. To install Mplayer, look for it in Adept, or from Konsole:
```
sudo apt-get install mplayer
```

---

