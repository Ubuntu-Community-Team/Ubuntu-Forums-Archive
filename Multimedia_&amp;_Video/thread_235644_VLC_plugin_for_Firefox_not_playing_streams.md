---
title: "VLC plugin for Firefox not playing streams"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by roguenoir on 2006-08-13
I've installed the VLC plugin for Firefox and it's not playing the streams on this site:  [www.askaninja.com](www.askaninja.com).  On my XP machine, they play perfectly fine, so it's not a network issue.  Here's a copy of the messages output I get when I copy the location of the video and try to play it using Open Network Stream:

> 
netsync error: master address not specified
main debug: creating new input thread
main debug: waiting for thread completion
main debug: `http://www.askaninja.com/ninja/revver/1244?width=320&height=278' gives access `http' demux `' path `www.askaninja.com/ninja/revver/1244?width=320&height=278'
main debug: creating demux: access='http' demux='' path='www.askaninja.com/ninja/revver/1244?width=320&height=278'
main debug: looking for access_demux module: 0 candidates
main warning: no access_demux module matched "http"
main debug: creating access 'http' path='www.askaninja.com/ninja/revver/1244?width=320&height=278'
main debug: looking for access2 module: 7 candidates
access_http debug: http: server='www.askaninja.com' port=80 file='/ninja/revver/1244?width=320&height=278
main debug: net: connecting to [www.askaninja.com](www.askaninja.com) port 80
main debug: thread 2977045424 (input) created at priority 0 (src/input/input.c:230)
main debug: connection in progress
access_http debug: protocol 'HTTP' answer code 206
access_http debug: Server: Apache/2.0.55 (Debian) mod_python/3.1.3 Python/2.3.5 PHP/4.4.2-1+b1 mod_perl/2.0.2 Perl/v5.8.8
access_http debug: Pragma: no-cache
access_http debug: stream size=982
access_http debug: Content-Type: text/html; charset=utf-8
main debug: using access2 module "access_http"
main debug: pre buffering
main debug: received first data for our buffer
main debug: creating demux: access='http' demux='' path='www.askaninja.com/ninja/revver/1244?width=320&height=278'
main debug: looking for demux2 module: 41 candidates
ps warning: this does not look like an MPEG PS stream, continuing anyway
main debug: using demux2 module "ps"
main debug: `http://www.askaninja.com/ninja/revver/1244?width=320&height=278' successfully opened
ps warning: garbage at input, trying to resync...
main debug: EOF reached
main debug: closing input
main debug: unlocking module "ps"
main debug: unlocking module "access_http"
main debug: thread 2977045424 joined (src/input/input.c:386)
main: nothing to play


---

### Post by -deadcats on 2006-08-13
That's why I'm not so thrilled with VLC. 

However, the mplayer-plugin works fine on that site.

regards,
-dc

---

### Post by ok67 on 2006-11-08
I upgraded to 6.10 a few days ago and after that I could not play any embeded video in Firefox. But after removing the entire VLC stuff I am able to play embeded videos again. However they are opened in an external gxine window, but that is OK.

---

