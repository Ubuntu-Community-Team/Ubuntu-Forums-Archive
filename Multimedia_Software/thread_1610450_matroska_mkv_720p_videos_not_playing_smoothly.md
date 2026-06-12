---
title: "matroska mkv 720p videos not playing smoothly"
date: 2010-10-31
forum: Multimedia Software
---

### Post by fremantle on 2010-10-31
i have acer 5532 with ati raden hd 3200. on windows xp, all 720p files play nicely in media player classic (with klite).. but when i switched to ubuntu, inoticed that SOME 720p videos are not playing smoothly at all (frame skipping..freezing etc) but the audio is ok-ish. after a bit research i found out that only the matroska avi/mkv HD files cannot be played smoothlly. i have installed the restricted extras and proprietary ati drivers. \\\
any suggestions?

---

### Post by gordintoronto on 2010-10-31
Try to eliminate any services you don't need, such as Bluetooth, and any programs you don't need to have running when you play videos. That CPU is pretty easy to overwhelm. The CNET Editor's review said, "Woeful performance, even for a budget laptop..."

---

### Post by kerry_s on 2010-10-31
gnome-mplayer

put:
```
-lavdopts skiploopfilter=all
```

in the extra options.

---

### Post by fremantle on 2010-10-31
> **gordintoronto said:**
> Try to eliminate any services you don't need, such as Bluetooth, and any programs you don't need to have running when you play videos. That CPU is pretty easy to overwhelm. The CNET Editor's review said, "Woeful performance, even for a budget laptop..."
trust me, reviews dnt always provide the absolute truth

---

### Post by jrz on 2010-12-11
I've noticed the same problem playing .mkv and found the total cpu usage 100% when playing with movie player, and vlc which both produce good audio but erratic video. I found xine was able to play .mkv with both good audio and video, but the total CPU usage was running 99%. An .avi copy of the same video file produced good audio and video using all 3 players and a CPU usage of 11% with each.

individual CPU usage playing .mkv file
movie player 35%
vlc 30%
xine 27%

individual CPU usage playing .avi version of the same file
movie player 11%
vlc 11%
xine 11%

---

