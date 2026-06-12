---
title: "Linux as Media Server?"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by DareArkin on 2010-01-09
I'm in the process of trying to set up a linux box (Read; Very basic- nothing more than a HD, network card, and motherboard) as a mini server, so that I can access all my movies and music whenever I want. But, alas, I know jack all about networking. How do I do this? How do I make it compatabile with Windows (As that's what my other pc still runs)?


Thanks in advance

Matt

---

### Post by Lars Noodén on 2010-01-09
If you want to just have files available, then Samba is probably the major way to go.  A very big barrier is the difficulty, and sometimes downright failure, of windows to support most standards.  Samba has a lot of extras that take into account those defects. 

If you want to stream audio and video, then you might be looking at icecast2 or videolan (vlc) instead.  

It's possible to have both Samba and VLC or Icecast2.

---

### Post by adam814 on 2010-01-09
Samba is indispensable in a general file/print sharing situation with Windows PCs.  I highly recommend it.

You might also want to try fuppes: [http://fuppes.ulrich-voelkel.de/faq/](http://fuppes.ulrich-voelkel.de/faq/).  It supports the Windows Media Streaming format I believe.  I use it to stream audio and video to my xbox 360 (I've heard it works with PS3 and WMP too).

---

### Post by Moozacman on 2010-02-02
I followed this to set up a nice and simple home server

[http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)

---

