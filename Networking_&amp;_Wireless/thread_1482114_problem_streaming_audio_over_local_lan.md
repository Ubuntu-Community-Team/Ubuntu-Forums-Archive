---
title: "problem streaming audio over local lan"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by ayushjsh on 2010-05-13
I am trying to stream an audio stream using vlc over a local lan which has just 2 PCs : 
mine on which I run the vlc and stream , my ip is 10.0.0.10 port 9988 uisng http
the other system is connected via lan cable and has ip 10.0.0.1
when I try to connect to the stream on the system with 10.0.0.1 I get 
vlc cannot connect to stream on [http://10.0.0.10:9988](http://10.0.0.10:9988)

I tried with udp as well and still no music. Both systems have ubuntu 9.10
plz help

---

### Post by kcode on 2010-05-15
See if [this]("http://www.videolan.org/doc/streaming-howto/en/ch04.html") helps.

---

### Post by viulian on 2010-05-17
I had a very similar problem. I explained it here: [http://forum.videolan.org/viewtopic.php?f=13&t=76380&p=251254#p251254](http://forum.videolan.org/viewtopic.php?f=13&t=76380&p=251254#p251254)

The problem is that my 9.10 was lacking some libraries, of which VLC did not complain about missing:

libmad0-dev
alsa-utils
libasound2-dev

I also compiled the x264 libraries from VLC's website.

After this, vlc 1.0.2 started to work.

[ps: I found them after a lot of work trying to get vlc 1.0.6 to compile and figuring out why enabled features by default, were actually silently disabled if the corresponding libraries were missing. 
Unless you force a feature (specify for example --enable-x264 to configure script, you don't get warned that the library is missing - so it falls back to disabled if you don't enforce it.
So I installed many things to get vlc to compile (qt4, alsa, yasm, etc) but I think those three libraries on top are the missing ones]

---

