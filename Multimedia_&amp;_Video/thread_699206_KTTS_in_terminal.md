---
title: "KTTS in terminal"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by Seb1982 on 2008-02-17
Hi everyone!

Yesterday evening i finally made KTTS work properly on my computer. But what i'd like to know now is how to use the TTS-system within a console. I remember that in OS X you had to type ```
say "Whatever!"
```.

---

### Post by luisromangz on 2008-02-17
KTTS is the KDE frontend for a number of text to speech programs that are command line, so they can be used by KDE apps.

You can still use the command line programs, for example festival:

 echo "Whatever!" | festival --tts

You can create easily a "say" script that insert its parameter as the text to be read.

---

### Post by Seb1982 on 2008-02-17
echo "Whatever!" | festival --tts does not work. Output:

```
seb@janee:~$ echo "Whatever!" | festival --tts
bash: !": event not found
```

Is there any other way?

---

### Post by Zorchenhimer on 2008-06-12
Remove the "!" so bash doesn't get confused.

---

