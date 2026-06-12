---
title: "[SOLVED] Sound in MPlayer, no sound with anything else"
date: 2008-06-01
forum: Multimedia Software
---

### Post by stromskij on 2008-06-01
Hello, I have searched around the forum and didn't find anyone with quite the same problem as me. 

I recently upgraded to Ubuntu 8.04, and now I get no sound in anything except Mplayer. No sound with flash or any of the other audio programs. I set the system to use alsa, and I actually get sound when I test it under sound properties. I set gstreamer to use alsa, I tried to recompile alsa, and I checked to see if sound was muted in alsamixer, but nothing helped. Mplayer is also using alsa.

Quite frustrating, can anyone help?

---

### Post by stromskij on 2008-06-02
...anyone? I don't manage to fix this!

---

### Post by wolfen69 on 2008-06-02
it sounds like a pulse audio problem. go [HERE]("http://ubuntuforums.org/showthread.php?t=776739") and try it. it fixed my sound problem.

---

### Post by stromskij on 2008-06-02
Thanks, I tried it, but it didn't solve it. Any other tips...? Don't want to have to use Windows. :p

---

### Post by stromskij on 2008-06-02
In fact, I think it sort of made it worse... Now, mplayer wont give me any sound either.

---

### Post by stromskij on 2008-06-03
...and suddenly, I realized that sound works! There was an update, maybe that did it, or maybe it was the fix suggested by wolfen69. Anyways, just great! :)

---

