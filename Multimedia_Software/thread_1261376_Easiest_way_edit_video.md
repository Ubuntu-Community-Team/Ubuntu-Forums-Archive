---
title: "Easiest way edit video"
date: 2009-09-08
forum: Multimedia Software
---

### Post by lesliek on 2009-09-08
I've downloaded a public domain movie said to be in format "512Kb MPEG4".

All I want to do is to extract from the movie one continuous segment that begins shortly after the movie's start and runs for a short while.

What software should I be using to do that in the easiest possible way? This will be a one-off exercise for me.

Thanks,

Leslie

---

### Post by rob-ward on 2009-09-08
You can use the application transcode to do that

```
transcode -c 0:3:15-0:4:00 -i inputfile -x auto,auto -y xvid -o outputfile
```

The numbers after -c  are the times so this command grabs the video from 0hours 3 minutes and 15 seconds in till the 4 minute mark, the -y option is the output type. 

Hope that helps

---

### Post by StuartN on 2009-09-08
Avidemux is easy to drive and has video / audio direct copy to just cut segments without transcoding.

---

### Post by lesliek on 2009-09-10
Thanks for your answers. I foolishly forgot to subscribe to my own question and so didn't find these answers till now!

Thanks again,

Leslie

---

