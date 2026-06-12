---
title: "Sound problem-clicking"
date: 2009-05-15
forum: Multimedia Software
---

### Post by pigsandribs on 2009-05-15
I just recently installed Linux Ubuntu 9.4, but am having a sound problem.  Whenever I open anapplication that requires sound, it starts clicking continuously, until I close the application.  I checked to make sure the computer was sensing the sound card, and it was, does anyone know what this problem might be?

---

### Post by unicycletim on 2009-05-15
Hey,
I had a similar problem recently.
all i did to fix it was open terminal, type 'alsamixer' and turn up the 'PCM' channel, and everything worked perfectly.
To navigate in alsamixer, use the right/left keys to change channel and up/down to increase/decrease volume

---

### Post by pigsandribs on 2009-05-15
I tried turning the PCM volume up to 100, but I'm still having the problem.  Since I posted I tried playing a music CD but it wasn't playing, when I did get it do get off two seconds and appearing like it would play, I had the same clicking problem.  I'm not sure i it's related or a completely different problem with the same symptoms.  The startup sound when I start Ubuntu chimes perfectly though.  Any other suggestions?

---

### Post by wimpelmeesje on 2009-05-15
Do you have an Intel soundcard? If so try to add that in your search. I had a similar problem which was solved by adding a line to the also config file. The solution is floating around on the forum somewhere, just don't remember where :/.

---

### Post by pigsandribs on 2009-05-22
I tried searching the forums to find that post, but failed.  Eventually I figured out how to update the alsa driver correctly, and now i have a different problem.  The clicking is gone, but I now have no sound.  However, before, when I attempted to play a video, it would play for a few seconds, then freeze, now I don't have this problem, videos will play normally.  I'm going to go back to searching the forums for a solution to this new problem, but if anyone has any ideas what might have happened during the update, feel free to mention thme here.

---

