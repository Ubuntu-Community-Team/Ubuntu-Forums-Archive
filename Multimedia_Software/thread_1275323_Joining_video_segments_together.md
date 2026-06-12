---
title: "Joining video segments together"
date: 2009-09-25
forum: Multimedia Software
---

### Post by rwandy on 2009-09-25
Join video parts.  I have 8 small parts of a complete avi video clip. The instructions were to join them together before the complete video would work.  What Ubuntu program will join them together?

---

### Post by lykeion on 2009-09-25
ffmpeg will do that...

see [http://ffmpeg.org/faq.html#SEC30](http://ffmpeg.org/faq.html#SEC30)

---

### Post by Marlonsm on 2009-09-25
There are quite some video editors you can use.

The best one, in my opinion, is Kdenlive. You can find it in Applications > Add/remove.

---

### Post by mocha on 2009-09-26
Do like this for avi files:

```
mencoder -oac copy -ovc copy INPUT1.avi INPUT2.avi -o COMBINED.avi
```

Just keep adding the INPUTx.avi in the order you want from first to last.  Note, if your COMBINED.avi file has audio sync problems, just re-do this but add -forceidx to the options.

---

### Post by cotcot on 2009-09-26
Avidemux has an "append" function to append 1 clip after another. The can save the result without re-encoding the clips (that is good because of quality loss). The terminal commands posted before also do not re-encode. Check with other video editors if the result is re-encoded or not.

---

