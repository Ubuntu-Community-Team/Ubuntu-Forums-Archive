---
title: "Stream DVB(-C) over lan/internet with VLC"
date: 2008-03-04
forum: Multimedia &amp; Video
---

### Post by sudo_t43p on 2008-03-04
Hi,

I have a working DVB-C card running under Ubuntu 7.10. Now my idea was to stream DVB-C over internet (and lan). I have read VLC tutorials but I am apparently too stupid to figure out how to stream this from command line.

Here is an example of what I want to stream:

#EXTINF:0,National Geographic
#EXTVLCOPT:program=201
#EXTVLCOPT:dvb-adapter=0
#EXTVLCOPT:dvb-frequency=434000000
#EXTVLCOPT:dvb-srate=6875000
#EXTVLCOPT:dvb-modulation=64

and here is what I have tried:

user@desktop:~$ vlc -vvv dvb: --dvb-frequency=434000000 --dvb-srate=6875000 --sout '#standard{access=http,mux=ogg,dst=some.server.com:8080}'

But I cannot get this to work. What should the command look like for streaming?

Thanx in advance!

BR,
Chrisse

---

