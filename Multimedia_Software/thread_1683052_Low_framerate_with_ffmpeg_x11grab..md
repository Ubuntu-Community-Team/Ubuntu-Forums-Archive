---
title: "Low framerate with ffmpeg x11grab."
date: 2011-02-06
forum: Multimedia Software
---

### Post by Senesence on 2011-02-06
Following this tutorial:

[http://ubuntuforums.org/showthread.php?t=1392026](http://ubuntuforums.org/showthread.php?t=1392026)

I got everything to work, but the running capture framerate is about half of that set (-r 30).

I'm stuck on getting something like 14 fps, which is noticeably choppy.

I have a relatively decent system (dual core intel), so I don't think I'm hitting the limitations of the machine (it's only using little over the single core during the process).

Anyone know what could be causing the problem, and how to fix it?

Thanks.

---

### Post by mocha on 2011-02-07
What is your exact command line?  "it's only using little over the single core during the process"  ??  Something isn't right.  It shouldn't hardly use any CPU.

---

### Post by Senesence on 2011-02-07
> **mocha said:**
> What is your exact command line?  "it's only using little over the single core during the process"  ??  Something isn't right.  It shouldn't hardly use any CPU.

This is the exact command:
```
ffmpeg -f alsa -ac 1 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv
```

I reasoned that high CPU load was due to the fact that video encoding (H.264) was being done on the fly.

---

### Post by Senesence on 2011-02-07
Bump - Anyone?

---

### Post by mocha on 2011-02-07
I just did a 1280x1024 capture at 30 fps and when I checked top it said ffmpeg was using a steady 125% of my 4 core system.  Are you using the ffmpeg from the repos?  I use a version compiled from SVN.  There is a thread on these forums explaining how to do it if you are interested.

---

### Post by FakeOutdoorsman on 2011-02-08
Can you show some more info on your CPU? The *model name* from "cat /proc/cpuinfo" will suffice. Also, the complete terminal output from FFmpeg could be useful too. Is it capturing at ~14 fps, or just playing back at 14 fps?

---

