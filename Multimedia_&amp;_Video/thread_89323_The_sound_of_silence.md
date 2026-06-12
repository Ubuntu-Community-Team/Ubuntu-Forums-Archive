---
title: "The sound of silence"
date: 2005-11-12
forum: Multimedia &amp; Video
---

### Post by opera on 2005-11-12
Dear anyone, I am new to linux, I am new to Ubuntu, and I am totally new to an operating system that doesn't support sound out-of-the-box! I have tried dozens of fixes to no help. Maybe I am rude, but how can an OS not support sound? Can someone please point me in the right direction or I most certainly will be back in the arms of M$ and Windoze. My soundcard is HDA ALC880.

---

### Post by teaker1s on 2005-11-12
make sure you have system-preferences-sound showing your soundcard
next  'volume control'  'file' 'change device' and select your card and alsa
next you need to make sure your aplication is using alsa or you will have no sound

---

### Post by opera on 2005-11-12
Thanx for helping out but there is still no sound, and jugding by all the other postings this seems to be a very common problem with (linux?) Ubuntu?

---

### Post by teaker1s on 2005-11-12
can you see your sound card listed?
if so then volume control-edit-preferences-select everything and now you will have all avaliable switches and can select outputs in the switches section of volume control

if you can't see your soundcard listed I would have a look on google  "the model and linux" see if you can see any previous attempts.

also be aware the branded card isn't  always the maker this can be seen by system-administration-device manager 

my trust 514dx is in fact a cmedia card

sorry I can't suggest more but I'm sure someone more in the know will has some suggestions

---

### Post by opera on 2005-11-13
"if so then volume control-edit-preferences-select everything and now you will have all avaliable switches and can select outputs in the switches section of volume control"

Teaker1s, thankU thankU !
This did it :-) I got sound.

---

