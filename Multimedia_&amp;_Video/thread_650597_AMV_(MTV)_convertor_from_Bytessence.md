---
title: "AMV (MTV) convertor from Bytessence"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by patslap on 2007-12-26
I am trying to install software from [http://www.bytessence.com/bamvc.html](http://www.bytessence.com/bamvc.html) 

I have d/l to Desktop. How can I use it? :confused:

The software is designed to convert video files to .AMV format for use on a Chinese MP3 player.

Thanks

---

### Post by jpkotta on 2007-12-26
You need to set the executable bit in the BAMVC file.  
```

cd BAMVC_LIN
chmod +x BAMVC
./BAMVC

```

---

### Post by patslap on 2007-12-27
Thanks  -this worked. I also had to make ffmpeg executable in the /Core directory of BAMVC_LIN.

Double-clicking on BAMVC then opens up the GUI to use the media converter.

Many thanks

---

### Post by jackchen on 2008-01-10
wow, it's a little technical, could have been better for beginners with screenshots to accompany. 

Anyway, tried the commands given by 'jpkotta' and also the reminder from 'patslap'.

Thanks guys, I managed to get it to work on my iPod Nano clone.

---

### Post by Tumpster on 2008-02-14
Hey there, I'm getting this error: "FFmpeg needs to exsist in the ./Core directory. Please copy it there and restart the converter." Ideas?


Disregard please, got it working after setting it to act as a program and now all runs smoothly, thanks!!!

---

### Post by Tumpster on 2008-02-24
When I convert em it's converting to AMV but after loading em on my chipod it runs slowly and choppy. Any ideas? Thanks!

---

### Post by Ripfox on 2008-04-01
Pardon me, but how exactly do you "make ffmpeg executable inside the bamvc directory?"

---

### Post by patslap on 2008-04-01
Open a terminal and change to /Core directory, then type ```
chmod +x ffmpeg
```

---

