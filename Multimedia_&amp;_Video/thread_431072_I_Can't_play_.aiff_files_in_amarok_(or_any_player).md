---
title: "I Can't play .aiff files in amarok (or any player)"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by anabelle on 2007-05-02
Hi, i have a bunch of .aiff files and i can't get them to play in any player, i've tried amarok, banshee, kaffeine, mplayer, but none is able to play them.

How can i add aiff support to amarok? or other player?


ive tried using sox to convert aiff to wav, but i have to convert file by file, and i find it really annoying and time waisting.


How can i playback .aiff easily on my ubuntu?

---

### Post by FilmAficionado on 2008-01-23
I know this is a super old post but I found it and alas, via a google search as well, found NO solution to getting AIFF files to play (in Amarok or any other player as well)...

Is there a solution to this (as in a specific codec one would need to install)?

Did you, or anyone else, ever figure this out?

Thanks!

(hope this bumps this up!)

---

### Post by wizard10000 on 2008-01-24
I can play aiff in totem and VLC.  Not sure this will help but You might try installing libaudiofile0 and libsndfile1.

---

### Post by ethridgt on 2008-02-11
I was able to convert ".aif" files using sound converter.  Maybe that will help.  

From the command line, enter this line:

sudo apt-get install soundconverter

---

### Post by Kulgan on 2008-02-16
Aiff will play in totem for me, but had to be added to the open-with list (Properties -> Open With -> Add -> Movie player") of an aiff file before it would open. No problems actually playing the files.

---

