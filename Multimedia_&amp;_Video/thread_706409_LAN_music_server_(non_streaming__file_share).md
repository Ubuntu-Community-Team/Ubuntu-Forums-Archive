---
title: "LAN music server (non streaming / file share)"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by m@ra on 2008-02-24
I have a setup of one Ubuntu server (no X installed) and one Windows laptop (work) + Ubuntu desktop. Now... I have stereos attached to my PC and I play music from there.  Here is the problem... If I'm using my laptop I can't play music cause stereo cable is attached to PC.

What would be ideal is of course to have music on server. And web interface to play that music (VLC has actually something like this). That would make possible to change music through WLAN from laptop - and server could serve it. But... I have so much music that I would require also a musiclibray support for this - so VLC interface is not good enough.  I do  have soundcard on my server.

I've tried to look for this... No solutions found yet. Mostly there is a fileserver where from I could download / stream music. 

All thoughts appreciated.

-markus

---

### Post by flybiwire on 2008-03-02
bump......

I'd really like to know a solution for this, too.  I'm brand spankin' new to Linux; i'm installing Ubuntu server on an older desktop as I type.  Same question:

I'd like to use the server connected to my stereo as my music server and player; I'd like to be able to control the music being played from a laptop via the home wireless LAN.  Is it possible?  Just trying to get around having to buy a Roku or air express and wanting to delve into the world of Linux.  Any help?

Muchos gracias!

---

### Post by BDNiner on 2008-03-02
Rhythmbox is able to play files that are located on network shares. I used to have all my music (14GBs) on my windows computer. I shared my music folder and was able to connect to the share from my ubuntu computer and mounted the folders to the desktop. Just go to "places" and then "connect to server..." and browse to the computer that has all the music. I could even put a music CD into my ubuntu PC and rip it and it would be copied to the my music folder on my windows computer. It would really slow down the wireless network though. If you decide to place the music on an ubuntu PC. then you would have to install samba so that your windows computer are able to browse to the music.

---

### Post by efgevh on 2008-03-03
probably plenty of solutions for this, and free and good too -  best on I've found is Ampache [www.ampache.org](www.ampache.org)
another is mpdwebamp  - python based.

Both lets you control your music from a browser
ampache collects album art, has lots of sorting, plays at least mp3, ogg, flac, use with your last.fm account and more..

---

### Post by efgevh on 2008-03-03
this firefox addon 

[http://code.google.com/p/musicpm/](http://code.google.com/p/musicpm/)

, is impressing. No need to install anything on the server. Addon just connects to servers mpd

---

### Post by flybiwire on 2008-03-09
Got it working, the music Minion for firefox is incredible!!  Thanks!

---

### Post by RebelwithoutaClue on 2008-03-23
I have given the name and the address of the server and share and I get nothing.

What should I put in to either open or browse the (windows) server?

All the excitement shown above makes it sound like a great replacement for the clunky rhytmbox but not if I can't see the server.

Also, does it do gapless and have a reasonable shuffle?

---

### Post by RebelwithoutaClue on 2008-03-23
Looking further into it I discover I've got to learn telnet commands to try and get to my server with this app.

What a crock.

I don't see this as a solution to the lack of half decent mp3 player that can cope with streaming across a LAN.

I'm sorry I even wasted my time looking at this - nice interface but zero useful.

---

