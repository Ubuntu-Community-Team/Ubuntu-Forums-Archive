---
title: "DeVeDe convert issue"
date: 2010-11-27
forum: Multimedia Software
---

### Post by Swagman on 2010-11-27
I have successfully converted ogv from Desktop Recorder to DiVx using DeVeDe without any problems but lately......

For some strange reason it's now only making a 9 second file ?

I've tried different options, Used Synaptic to do a complete removal...Reboot and re-install... Created a live USB and installed Desktop recorder and DeVeDe in it... DeVeDe worked properly **ONCE**


Gave up and used (Tried to) VLC... What a catastrophe that is/was !!

Anyone got any clues please as I'm all out of ideas !!

---

### Post by ron999 on 2010-11-27
> **Swagman said:**
> 
Gave up and used (Tried to) VLC... What a catastrophe that is/was !!

Anyone got any clues please as I'm all out of ideas !!

Try converting the file using FFmpeg with a command like this:-
```
ffmpeg -i filename.ogv -vcodec libxvid -b 1500k -acodec libmp3lame -ab 128k output.avi
```

---

### Post by MepisReign on 2010-11-27
DeVeDe uses Mencoder, maybe trying to install it from their SVN?

[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

Best Regards

MepisReign

---

### Post by Swagman on 2010-11-27
Thanks chaps will give it a try. I subscribed to this thread with instant email notification but never received any ?

Problems.. What would life be like without them !

---

### Post by Swagman on 2010-11-27
> **ron999 said:**
> Try converting the file using FFmpeg with a command like this:-
```
ffmpeg -i filename.ogv -vcodec libxvid -b 1500k -acodec libmp3lame -ab 128k output.avi
```

Winner !!

:D

Just needed to boost the resolution.


Haven't tried the Mencoder route yet though.

---

