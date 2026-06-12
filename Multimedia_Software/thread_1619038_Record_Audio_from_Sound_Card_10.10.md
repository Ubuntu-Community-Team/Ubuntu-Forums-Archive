---
title: "Record Audio from Sound Card 10.10"
date: 2010-11-11
forum: Multimedia Software
---

### Post by insanekat on 2010-11-11
I can't seem to get my computer to record the audio from an application... Sound Recorder, Audacity, and outRec all output files but they are just silence, even though when I see them in a media player they show the visualizations. 

I have followed a couple guides to no avail. Hopefully someone can help me out!

Thanks

---

### Post by lidex on 2010-11-11
> **insanekat said:**
> I can't seem to get my computer to record the audio from an application... Sound Recorder, Audacity, and outRec all output files but they are just silence, even though when I see them in a media player they show the visualizations. 

I have followed a couple guides to no avail. Hopefully someone can help me out!

Thanks

Have you seen this:
[http://ubuntuforums.org/showthread.php?t=1005196](http://ubuntuforums.org/showthread.php?t=1005196)

---

### Post by insanekat on 2010-11-12
I just gave that a try but 2 things:
1. When I go to System>Preferences>Sound, I do not see an option anywhere for Pulse Audio
2. I went on with the guide anyway, however I played things through a few applications and it did not show up in the Pulse Volume Meter

---

### Post by lidex on 2010-11-12
> **insanekat said:**
> I just gave that a try but 2 things:
1. When I go to System>Preferences>Sound, I do not see an option anywhere for Pulse Audio
2. I went on with the guide anyway, however I played things through a few applications and it did not show up in the Pulse Volume Meter

It's changed a bit. Try this in a terminal:
```
gstreamer-properties
```

---

### Post by insanekat on 2010-11-13
Ah that's all it took! Thank you it works now!

---

