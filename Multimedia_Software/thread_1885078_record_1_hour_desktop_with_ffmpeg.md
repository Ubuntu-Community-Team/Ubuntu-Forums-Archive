---
title: "record 1 hour desktop with ffmpeg"
date: 2011-11-22
forum: Multimedia Software
---

### Post by MRnico on 2011-11-22
need to record my desktop to a file using ffmpeg
I already am doing.

my question is:

How I can record 1 hour of video and then stop recording and start over?

---

### Post by boast on 2011-11-22
how about [http://help.ubuntu.com/community/CronHowto](http://help.ubuntu.com/community/CronHowto)

---

### Post by MRnico on 2011-11-23
thanks for your answer, but i need some specific instructions

now i have this script that work, but not always

any way to do a better script?



```
echo "/bin/kill -HUP $$" | at now + 60 minutes
/home/user/ffmpeg/ffmpeg -f x11grab -r 15 -s 1280x800 -i :0.0 -vcodec libx264 -p
reset ultrafast -crf 0 -threads 0 /home/user/output1.mkv
mv /home/user/output1.mkv /home/user/video`date +%F_%T`.mkv
```

---

### Post by FakeOutdoorsman on 2011-11-24
One option to consider is adding -t 01:00:00.00 or -t 3600 (same thing, but in seconds) to your ffmpeg command to make a recording one hour long, and then the command can be looped in a bash script or added to your hourly crontab (although there might be some overlap by a second or two with the cron method but it should be "on the hour").

I'm not sure how arbitrarily killing the ffmpeg process with kill would affect the output as your method does, but -t might be a "cleaner" method as it allows ffmpeg to complete the video normally.

---

