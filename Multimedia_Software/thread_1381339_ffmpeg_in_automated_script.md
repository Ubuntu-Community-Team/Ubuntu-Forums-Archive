---
title: "ffmpeg in automated script"
date: 2010-01-14
forum: Multimedia Software
---

### Post by sn0m on 2010-01-14
Hi Guys
I would appreciate if any of you could tell me how to force ffmpeg to be really quiet.
I want to convert a bunch of wmv and flv videos which I have downloaded from internet to a mp4 format, so I can play them in my Nokia 5800.
This is command line that works perfectly:

ffmpeg -i "input.avi" -f mp4 -vcodec libxvid -s 640x360 -b 768kb -r 25 -aspect 16:9 -acodec libfaac -ab 96kb -ar 44100 -ac 2 "output.mp4"

My question:
Is there a way to make it really quiet so I can run it from cron..

Many thanks

Sokol

---

### Post by FakeOutdoorsman on 2010-01-14
> **sn0m said:**
> Hi Guys
I would appreciate if any of you could tell me how to force ffmpeg to be really quiet.
I want to convert a bunch of wmv and flv videos which I have downloaded from internet to a mp4 format, so I can play them in my Nokia 5800.
This is command line that works perfectly:

ffmpeg -i "input.avi" -f mp4 -vcodec libxvid -s 640x360 -b 768kb -r 25 -aspect 16:9 -acodec libfaac -ab 96kb -ar 44100 -ac 2 "output.mp4"

My question:
Is there a way to make it really quiet so I can run it from cron..

Many thanks

Sokol

You could shut-up FFmpeg with **> /dev/null 2>&1**, as in:
```
ffmpeg -i "input.avi" -f mp4 -vcodec libxvid -s 640x360 -b 768kb -r 25 -aspect 16:9 -acodec libfaac -ab 96kb -ar 44100 -ac 2 "output.mp4" > /dev/null 2>&1
```
Unfortunately, you won't get any error messages if anything fails.  You could also output any messages to a log file instead of just dumping any output to */dev/null*.

---

### Post by sn0m on 2010-01-15
Yes but will that execute in cron?

---

