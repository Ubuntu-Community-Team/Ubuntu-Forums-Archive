---
title: "Picture height wrong on playback"
date: 2015-11-11
forum: Mythbuntu
---

### Post by alan44 on 2015-11-11
I have Mythbuntu with the latest updates. The picture size is fine when we watch programs live, but when we watch the recording of the same program, the picture is the correct width but is only about 3/4 of the proper height. nVidia video card (can't recall the number, but it's one that was recommended specifically for Mythbuntu), Samsung HDTV (1920x1080p).

I haven't found any setting that I recognize as being able to fix the problem.

---

### Post by alan44 on 2015-11-11
Sorry! I realize that I had been looking at Live TV with Vertical Fill  selected but with Fill/Stretch/whatever "Off" when playing recordings. I  can fill the screen when either watching Live TV or playing a recording *as long as I select Vertical Stretch/Fill or "Full"* -- but then I am  losing varying amounts of the picture off the left and right of the  screen as well.

In other words, although 1920x1080 is selected everywhere I can see, the picture height is insufficient unless I Stretch or Fill.

---

### Post by blm-ubunet on 2015-11-11
Not connected by VGA ?

Post your /var/log/Xorg.0.log file and mythfrontend log (as attached files).
You may have to launch mythfrontend from a terminal & redirect stdout to file
mythfrontend.real -v playback > mylogfile.txt

---

### Post by alan44 on 2015-11-12
> **blm-ubunet said:**
> Not connected by VGA ?

Post your /var/log/Xorg.0.log file and mythfrontend log (as attached files).
You may have to launch mythfrontend from a terminal & redirect stdout to file
mythfrontend.real -v playback > mylogfile.txt

HDMI connection.

Archived .log files attached:

[ATTACH]265528[/ATTACH] 

I played a few seconds of an HDTV recording and switched fill/stretch settings while doing so. Whether that shows up in the log file I don't know.

---

### Post by blm-ubunet on 2015-11-12
1280x540 29.97Hz progressive scan.. how did this happen?
Do you have some transcode script set to automatic run on recording?
HDPVR encode recording in the same video "dimension/size" as original source.

Can you probe the actual recording file with mediainfo or ffprobe?

Maybe collect frontend log for liveTV.

---

### Post by alan44 on 2015-11-15
I found a settings screen in mythfrontend that I don't recall seeing  before. I changed some settings that looked weird, and now everything  seems to be A-OK now.

---

