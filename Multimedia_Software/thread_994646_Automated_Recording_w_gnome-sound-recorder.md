---
title: "Automated Recording w/ gnome-sound-recorder?"
date: 2008-11-26
forum: Multimedia Software
---

### Post by fisherm on 2008-11-26
I'm looking for a way to automatically start a recording at 1300hrs and stop at 1600hrs using the line-in input. Also I need to save the file as RadioShowNameDDMMYYY.ogg. Trying to figure out command line controls for gnome-sound-recorder so I can put together a script to do this job. Thanks

---

### Post by talsemgeest on 2008-11-29
If you want to find all the commands for gnome-sound-recorder, simply type ```
man gnome-sound-recorder
```
and once you have the command you need to run, you can schedule it to run when you want using cron:

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Hope this helps :)

---

### Post by mocha on 2008-11-29
Actually it's better to use arecord and setup a cron job.  I do the same thing as you're talking about.  arecord is nice since then you can pipe it to lame and make a realtime MP3.

---

