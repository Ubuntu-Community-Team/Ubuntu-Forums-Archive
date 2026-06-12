---
title: "Amarok problem: mp3 not supported"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by Lelouch on 2007-08-23
"mp3 not supported"

I get this error every time i try to play a mp3 file... and then, amarok stops responding

I installed all the necessary codecs to play mp3 files...

Please help

---

### Post by DrumScum on 2007-08-23
> **Lelouch said:**
> "mp3 not supported"
I get this error every time i try to play a mp3 file... and then, amarok stops responding

Known Amarok bug is Feisty.

> **Lelouch said:**
> 
I installed all the necessary codecs to play mp3 files...
Please help

I guess you didn't. Try:
```

sudo apt-get install libxine-extracodecs
```

---

### Post by Lelouch on 2007-08-23
it is a little strange but.... amarok couldn't start now!!

---

### Post by gsmith on 2007-08-23
Had same problem, this solution worked for me.

---

### Post by Skorzen on 2007-08-25
> **gsmith said:**
> Had same problem, this solution worked for me.

Worked with me too. Thanks a lot, DrumScum.

---

### Post by Ritchstorm on 2007-08-25
Hmm I had this problem as well and after whacking that code into the terminal, tried running Amarok and nothing happens. It looks as if it's about to open a box but then nothing appears.

---

### Post by Ritchstorm on 2007-08-25
Ok well I turned off my PC and went out for a few hours and I just got back in and Amarok works now. I think it needs a restart after doing that command. Working all well with MP3's :guitar:

---

### Post by NovaAesa on 2007-08-26
worked here too (^_^)

---

