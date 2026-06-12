---
title: "Mpd"
date: 2008-12-20
forum: Multimedia Software
---

### Post by Demios101 on 2008-12-20
I've been using mpd+gmpc for quite a while and I love it, I have a simple questionthough. I can control the mpd server from multiple PCs that have clients installed, I have not yet been able to figure out how to listen to my music wherever I am. Can anyone explain to me how to do this?

---

### Post by jay li on 2008-12-20
I think you need to insert a name and password, so you make them all connected together.

---

### Post by Demios101 on 2008-12-21
> **jay li said:**
> I think you need to insert a name and password, so you make them all connected together.


Not at all, connecting to MPD gives me control of it on the pc it is on. I cannot listen to the audio.

---

### Post by qball on 2008-12-24
[http://mpd.wikia.com/wiki/What_MPD_Is_and_Is_Not](http://mpd.wikia.com/wiki/What_MPD_Is_and_Is_Not)

mpd plays on the machine it is installed on. It main purpose is not to stream to the clients.

You can make mpd stream to the network using icecast/shoutcast (re-encodes and has a delay) or pulseaudio (pulseaudio an broadcast to local network) but requires a somewhat reliable network.

---

