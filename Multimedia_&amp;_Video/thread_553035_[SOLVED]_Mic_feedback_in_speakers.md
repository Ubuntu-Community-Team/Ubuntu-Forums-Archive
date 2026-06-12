---
title: "[SOLVED] Mic feedback in speakers"
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by abhilash82 on 2007-09-17
I am getting a feedback from my mic, mostly noise which is very pronounced in my speaker output. This problem started only few days back and I am not able to remember as to which library package that I installed recently that would affect this. Can it be due to the Alsa Mixer settings?
:confused:

---

### Post by abhilash82 on 2007-09-21
Can anyone help me out with the Also mixer settings? Any documentation available for that?

:lolflag:

---

### Post by yabbadabbadont on 2007-09-21
Open a terminal window.  Run alsamixer.  Use the Tab key to switch to the capture levels.  Try lowering the level of your microphone to see if it helps with the feedback.  Hit Escape to exit alsamixer.

Edit: in alsamixer, use the arrow keys to move left and right and to raise and lower the levels.

---

### Post by abhilash82 on 2007-10-01
I was able to cancel out the mic feedback by reducing the capture settings in ALSA mixer but now my total sound is not working. I have posted it seperately [here]("http://ubuntuforums.org/showthread.php?t=557897").

---

