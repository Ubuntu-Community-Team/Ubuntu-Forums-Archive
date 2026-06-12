---
title: "Can't turn off microphone"
date: 2010-04-21
forum: Multimedia Software
---

### Post by jheis on 2010-04-21
I've got 9.10 installed on a dual boot T-43 Thinkpad.

The Thinkpad has a built-in microphone which is driving me crazy.  I have a pair of outboard Sony speakers sitting on my desk & the sound of the fan and every keystroke is picked up by the mic and amplified back at me through the speakers.  If I turn the volume on the speakers up more than about half way the mic picks up the feedback I get a high pitched squeal through the speakers.

I've gone into "Sound Preferences" and muted "Input Volume,"  but it has no effect - the mic is still picking up and amplifying every keystroke & giving me feedback.

How can I turn off the damn mic?  (by the way, I do not have this problem if I boot into XP)  Thanks.

James

---

### Post by lidex on 2010-04-23
Try alsamixer:
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.

---

### Post by Deathwish238 on 2010-04-27
Thank you, this is truly helpful. Alsamixer finally let me turn off the mic so I can turn the speaker voume up without hearing feedback.

Weird bug.

---

