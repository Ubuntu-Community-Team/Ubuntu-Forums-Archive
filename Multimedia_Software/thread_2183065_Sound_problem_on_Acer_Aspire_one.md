---
title: "Sound problem on Acer Aspire one"
date: 2013-10-23
forum: Multimedia Software
---

### Post by DaDark on 2013-10-23
Hi all!

I tried to install xubuntu (12.04) on an old acer aspire one netbook. Everything works fine except the sound. It's weird because when I try to listen to music, the sound is chopped. Moreover  I try to listen to music on banshee and grooveshark, and the time bar for both application, move faster than usual (one second seems 0,5 seconde or less!!). Sound is the same on speaker or if I plug headphones. 

I've try to remove pulseaudio and use only alsamixer but it's worse (I've got no sound at all after removing pulseaudio even if the speaker are well activated with alsamixer).

Any idea?

---

### Post by Yellow Pasque on 2013-10-23
[https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

---

### Post by DaDark on 2013-10-23
Great!!!!! Works perfectly now! Thank you!
I edit the alse-base.conf file and added : 
options snd-hda-intel position_fix=1

---

### Post by mörgæs on 2013-10-23
Good, then please mark the thread 'solved'.

---

### Post by DaDark on 2013-10-24
Ouuups!!!!

---

