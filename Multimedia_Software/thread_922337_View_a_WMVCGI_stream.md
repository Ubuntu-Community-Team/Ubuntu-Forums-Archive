---
title: "View a WMV/CGI stream"
date: 2008-09-17
forum: Multimedia Software
---

### Post by nielsl on 2008-09-17
Dear everybody,

I have Hardy 8.04 installed with vlc media player. I want to watch a stream on the internet ([http://streams.planet.nl/cgi-bin/reflector_tkstream.cgi?stream=3&title=Tweede%20Kamer%20der%20Staten-Generaal](http://streams.planet.nl/cgi-bin/reflector_tkstream.cgi?stream=3&title=Tweede%20Kamer%20der%20Staten-Generaal)) 

It just stops playing, well, it doesn't even start. Down you'll see a dump of the messages vlc gives me, I just don't know what is wrong (something with a demuxer?) It's probably something very small but i'm probably looking over it. Hope somebody can help!

thx
Niels

access_http debug: protocol 'HTTP' answer code 301
access_http debug: stream size=240
access_http debug: Content-Type: text/html; charset=iso-8859-1
access_http debug: Server: Apache
access_http debug: redirection to [http://www.kpnvandaag.nl/planet/](http://www.kpnvandaag.nl/planet/)
access_http debug: http: server='www.kpnvandaag.nl' port=80 file='/planet/
main debug: net: connecting to [www.kpnvandaag.nl](www.kpnvandaag.nl) port 80
main debug: connection in progress
access_http debug: protocol 'HTTP' answer code 206
access_http debug: stream size=3017
access_http debug: Content-Type: text/html; charset=utf-8
access_http debug: Server: Apache
main debug: using access2 module "access_http"
main debug: pre-buffering...
main debug: received first data for our buffer
main debug: creating demux: access='http' demux='' path='213.75.12.62/3'
main debug: looking for demux2 module: 45 candidates
ffmpeg debug: couldn't guess format
ps warning: this does not look like an MPEG PS stream, continuing anyway
main debug: using demux2 module "ps"
main debug: `[http://www.kpnvandaag.nl/planet/](http://www.kpnvandaag.nl/planet/)' successfully opened
ps warning: garbage at input, trying to resync...
main debug: EOF reached
main debug: closing input
main debug: removing module "ps"
main debug: removing module "access_http"
main debug: thread 3012987792 joined (input/input.c:412)
main: nothing to play

---

