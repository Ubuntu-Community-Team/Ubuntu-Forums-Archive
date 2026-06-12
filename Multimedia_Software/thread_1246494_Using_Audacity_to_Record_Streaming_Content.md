---
title: "Using Audacity to Record Streaming Content"
date: 2009-08-21
forum: Multimedia Software
---

### Post by chome4 on 2009-08-21
How do you set up Audacity to record streaming content?

---

### Post by tgalati4 on 2009-08-21
You can simply use arecord whateveriscomingoutofthespeakers.wav

Control-C to quit.

You can discover what devices arecord can see:

arecord -l

man arecord

If it's an mp3 stream, you can use streamripper.

With audacity, you need to set the mixer channels appropriately and monitor the master output such that you can see the sound levels in audacity.  There is a recording channel selector in the pull-down list.

---

### Post by chome4 on 2009-08-21
Thanks for that. I'll get on it later.

I couldn't see any sound levels when I did try and record from a streaming site so I'll fiddle about with levels.....

---

### Post by chome4 on 2009-08-22
I'm getting waveform output but only visually. The input level meter is registering during recording and the output level shows signs of live but nothing out of the speakers.

What do I need to check/change/adjust to get some noise?

---

