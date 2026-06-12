---
title: "Mythbunu 14.04.2 no video playing avi, mkv or mp4"
date: 2015-05-09
forum: Mythbuntu
---

### Post by MrEgg on 2015-05-09
Hello,

With a fresh install of Mythbuntu 14.04.2 on a Brix i5-5200U, I get no video playback with AVI, MKV or MP4 files (sound is ok) and no video with Live TV / recorded programs (sound is ok), *if and only if* I have previously played an M4V video. M4V files play normally (video and sound are ok). After a reboot, everything works fine. But this faulty behavior appears to come back again after playing any M4V video.

I did not experience this behavior on my previous old build of Mythbuntu 10.04.

Any idea as to what could be going on here?

Thanks,
Egg

---

### Post by blm-ubunet on 2015-05-10
If you are using opengl2/vaapi video playback then could be this bug (just fixed in 0.27)
[http://www.gossamer-threads.com/lists/mythtv/commits/586299](http://www.gossamer-threads.com/lists/mythtv/commits/586299)

A temporary work-around could be to just use CPU decode (ffmpeg-opengl).

Else need to look in the log files /var/log/mythtv/*.log &/or set more verbose logging options.
Could just start mythfrontend.real from terminal & redirect or watch ...
(Mythbuntu renames & wraps the real mythfrontend app in a script)

---

### Post by MrEgg on 2015-05-16
Thank you for you suggestion. It solved my issue.

Kind regards,
Egg

---

