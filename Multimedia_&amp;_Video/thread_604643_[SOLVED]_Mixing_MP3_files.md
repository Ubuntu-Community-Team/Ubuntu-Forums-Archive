---
title: "[SOLVED] Mixing MP3 files"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by AlistairH on 2007-11-06
I want to merge a number of mp3 files into one large mp3 file. Audacity allows my to paste one file onto the end of another but that's not what I want to do as the tail end of the first file gets chopped. I want to merge the files so that the end of the first merges into the start of the next.

Is there any audio editing software out there that you could recommend that does this?

---

### Post by tgalati4 on 2007-11-06
>sudo apt-get install sox
>man sox

---

### Post by AlistairH on 2007-11-06
Thanks, I'll have a look at that tonight

---

### Post by rsambuca on 2007-11-06
I have never seen audacity 'chop off the end" of a file, but if you want something easy, just use the command line.  You can merge as many mp3's together as you want:

cat file1.mp3 file2.mp3 file3 mp3 > output.mp3

---

### Post by AlistairH on 2007-11-07
I had a look at sox, but couldn't see how to make it do what I want it to do using command line options. Similarly, using 'cat file' on the command line will simply tag one mp3 file directly onto the end of another.

Ideally I'd like a graphical interface that will allow me to easily select how much of the end of the first track will be 'mixed' with the the beginning of the first track so that one fades into the other.

---

### Post by rsambuca on 2007-11-07
Audacity will do exactly that.  You just create a multi-track project, use the fade-in/fade-out feature at the ends and beginnings of your songs, and then line them up and export it to your desired format.

---

### Post by AlistairH on 2007-11-07
Brilliant rsambuca. Just tried it, once I found my way round Audacity a bit better. Worked a treat. Thank you.

---

### Post by rsambuca on 2007-11-07
Good stuff!  You may as well mark the thread as [solved].  It is under the thread tools options.

---

