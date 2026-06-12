---
title: "How to play pcm files?"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by edmondt on 2007-03-18
I think I have most of the codec installed, but I can't seem to play *.pcm files, from sjphone. I have attached the file. Can someone advice on how to fix this issue?

---

### Post by Gannin on 2007-03-18
I think you'll have to import it as raw data in Audacity.

---

### Post by edmondt on 2007-03-18
Or do I somehow have to register them as audio files? I can play everything else, mp3, wmv, ogg, rmvb etc...

When I get a phone call on SJphone, it doesn't ring so its very annoying (But I can speak to the person after etc).

---

### Post by edmondt on 2007-03-18
Bump... Please help. Can anyone play the files I attached?

---

### Post by Gannin on 2007-03-19
They're not easily playable by a third-party application because they're raw audio data files.  Nevertheless, if they're part of a program, then it doesn't matter what players or file associations you have on your computer, the program that they're a part of should play them.  If the program that they're a part of doesn't play them as it should, then that means there's a problem with that specific program.

---

### Post by madeddie on 2008-02-03
A bit late, but if anybody gets here via google or something;

cat filename.pcm > /dev/dsp

same goes for all raw audioformats. Quality might not be best, but at least you can hear them.

btw, your particular problem, sjphone on linux uses the PC speaker to play the ringtone, please check if the PC speaker works for you.

---

