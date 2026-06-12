---
title: "Putting Together a Song"
date: 2010-04-11
forum: Multimedia Software
---

### Post by Martin Marshalek on 2010-04-11
Okay, I've been working on making a relatively simple song for a Music Theory class that I am taking but I have a few problems. First off, I am using a cable to go from my keyboard output to my microphone port on my computer. It records and all but there is a microphone hiss with it. How does one go about removing this with Audacity? Also, when recording, there is no way to hear what I am playing. Is there a way to route the audio input to simultaneously play out through the speakers? When I am done with that much, I plan to run my recordings and such through Jokosher. For some reason though, it spits out a gstreamer error when I play anything yet I don't know why. Is there a solution for this somewhere or another similar program that I can use? 

Thanks for the help.

---

### Post by Martin Marshalek on 2010-04-11
For the Jokosher thing, this comes up in the console when I run it via terminal:

```
(jokosher:2200): GStreamer-WARNING **: Name recording bin is not unique in bin timeline, not adding
Traceback (most recent call last):
  File "/usr/share/jokosher/Jokosher/JokosherApp.py", line 478, in Record
    self.project.Record()
  File "/usr/share/jokosher/Jokosher/Project.py", line 374, in Record
    self.mainpipeline.add(recordingbin)
gst.AddError: Could not add element 'recording bin'
```

---

### Post by Chronon on 2010-04-11
> **Martin Marshalek said:**
>  Also, when recording, there is no way to hear what I am playing. Is there a way to route the audio input to simultaneously play out through the speakers? 

Check your mixer.  You should be able to hear the audio if "line in" is turned up.  If you can get more signal then the hiss should be less noticeable (i.e. better SNR).  This is usually preferable to attempting to remove hiss in post-processing.

---

### Post by Martin Marshalek on 2010-04-11
Thanks, I can now hear it! That was quite simple too.

---

### Post by Chronon on 2010-04-11
You're welcome.  :)

Regarding the jokosher error, it seems to be this bug:
[https://bugs.launchpad.net/ubuntu/+source/jokosher/+bug/349908](https://bugs.launchpad.net/ubuntu/+source/jokosher/+bug/349908)

---

### Post by Elleo on 2010-04-11
The error Martin's experiencing is fixed in version 0.11.5 which you can download here: [http://launchpad.net/jokosher/trunk/0.11.5/+download/jokosher_0.11.5-0ubuntu1_all.deb](http://launchpad.net/jokosher/trunk/0.11.5/+download/jokosher_0.11.5-0ubuntu1_all.deb)

---

