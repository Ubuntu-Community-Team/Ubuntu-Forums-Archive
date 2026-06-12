---
title: "How to capture sound sample from movie?"
date: 2007-09-09
forum: Multimedia Production
---

### Post by m666 on 2007-09-09
I need to record a 10 seconds long sound sample  from avi file (100 min long divx movie). How can I do that? Audacity doesn't allow this.

---

### Post by distroman on 2007-09-09
One way would be. 

Use avidemux to cut out the part you want. Open the avi with avidemux, then use the "A: Selection: start / B: Selection : end" to set the insert points.
Then "File > Save > Save video" remember to add the extension of the output file ".avi" in this case.

```
ffmpeg -i input.avi -ab 192 -ar 48000 output.wav
```
As an example to extract the audio to wav. 
Google on extracting audio if you want to see the options.

gl

---

### Post by m666 on 2007-09-10
I know avidemux. It doesn't seem to be very convinient way but I'll give it a try. Thanks for help!

---

