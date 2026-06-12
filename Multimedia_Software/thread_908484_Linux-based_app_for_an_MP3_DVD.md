---
title: "Linux-based app for an MP3 DVD"
date: 2008-09-02
forum: Multimedia Software
---

### Post by Tom_ZeCat on 2008-09-02
I use MP3 DVDs to play music in any DVD player when I'm traveling (without a laptop).  Thus far I've made them either in Roxio Easy Media Creator or in MediaMonkey, both of which are Windows-based.  However, now I'm using Ubuntu Linux 8.04 with Amarok 1.4 as my music system with my entire music collection on my Linux machine.  I tried to find a way to create an MP3 DVD on this machine, but couldn't.  I don't see any way to do it in Amarok or in the other audio software that I have, those being: Brasero Disk Burning, K3b, K9 Copy, and Audacity.  

Almost all my music is in the MP3 format, the exception being a few albums that are in OGG.  

Can an MP3 DVD be made with any of the software I have?  If not, what Linux software is capable of making an MP3 DVD.

---

### Post by wolfen69 on 2008-09-02
for k3b, do ```
sudo apt-get install libk3b2-extracodecs
``` you should then be able to burn mp3's as an audio cd/dvd. make sure to have all repositories enabled first.

---

