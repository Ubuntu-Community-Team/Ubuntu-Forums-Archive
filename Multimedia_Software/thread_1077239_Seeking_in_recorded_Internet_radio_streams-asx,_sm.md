---
title: "Seeking in recorded Internet radio streams-asx, smi"
date: 2009-02-22
forum: Multimedia Software
---

### Post by Barely Here on 2009-02-22
My clients (parents :-) spends a lot of time listening to recorded Internet radio from rthk, a public broadcaster in Hong Kong. For whatever reasons this station is using Internet streaming in asx (windows media) and smi (real) formats for recorded radio shows, rather than individual podcast download. My clients also seek within these radio streams, by jump forward or moving backward within the show.

I've installed the restricted-extras package for the codec support, but the default Totem player cannot seek within the streaming radio. I've also tried mplayer, but I cannot make it work in the GUI.

In the end, I've to install Real Player to enable seek within such recorded streaming radio. This worked fine in an older xubuntu and Real Player version.

However when I upgraded to Real Player 11 with xubuntu 8.04, the seek/progress bar disappeared from the player. Even though when I click in the progress bar 'area', the player can still jump to the segment. So it is still possible to seek, but it involves some guess work.

Anyway, because I'm too lazy to go out of Medibuntu to get a older version of Real Player, my clients just have to live with this inconvenience for a while :-P

---

### Post by vinutux on 2009-08-02
1. uninstall realplayer from mediubuntu

2. download deb from official site [http://www.real.com/linux](http://www.real.com/linux)

3. install deb if you are running 32 bit...if you are running 64 bit

right click extract here....

4. open extracted folder ...again right click extract data folder

5. open extracted data folder /opt/real/RealPlayer ...and run realplay ...it run smoothly

6. copy Realplay folder to somewere...like /opt (with gksu)...or home folder and make a launcher in menus

---

