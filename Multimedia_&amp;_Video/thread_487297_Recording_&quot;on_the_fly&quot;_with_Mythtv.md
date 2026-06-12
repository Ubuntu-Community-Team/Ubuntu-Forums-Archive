---
title: "Recording &quot;on the fly&quot; with Mythtv"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by Super TWiT on 2007-06-28
I have been trying to convert some VHS tapes to DVD using Mythtv, however when I hit the R button on my keyboard after I start watching T.V. It it only schedules a recording.  However,  when I try to view my recordings one file shows up, but Mythtv says it's not a recording.  I might be wrong about that only being a schedule.  There must be something really basic that I am missing.

---

### Post by superm1 on 2007-06-30
> **Super TWiT said:**
> I have been trying to convert some VHS tapes to DVD using Mythtv, however when I hit the R button on my keyboard after I start watching T.V. It it only schedules a recording.  However,  when I try to view my recordings one file shows up, but Mythtv says it's not a recording.  I might be wrong about that only being a schedule.  There must be something really basic that I am missing.

What station do you have it set to when doing this?  You likely need to use the "Schedule custom recording" option.

---

### Post by awells527 on 2007-06-30
If you want to do it a manual way, this thread will help you out: [http://www.mythtvtalk.com/forum/viewtopic.php?p=9491](http://www.mythtvtalk.com/forum/viewtopic.php?p=9491)

Specifically, the following command will do the trick

```
cat /dev/video0 > <filename> 
```

The output file will be in MPEG format.  Just enter that command with MythTV closed when you want to start recording, and CTRL + C it when you want it to stop.

---

### Post by superm1 on 2007-06-30
> **awells527 said:**
> If you want to do it a manual way, this thread will help you out: [http://www.mythtvtalk.com/forum/viewtopic.php?p=9491](http://www.mythtvtalk.com/forum/viewtopic.php?p=9491)

Specifically, the following command will do the trick

```
cat /dev/video0 > <filename> 
```The output file will be in MPEG format.  Just enter that command with MythTV closed when you want to start recording, and CTRL + C it when you want it to stop.
Assuming he has a mpeg2 encoding tuner yes, this will work and probably be a bit more straightforward.

---

### Post by Super TWiT on 2007-06-30
My T.V. card doesn't have an encoder on it.  Xawtv won't work for me, because it has no sound.  Otherwise, I would use that program.

---

