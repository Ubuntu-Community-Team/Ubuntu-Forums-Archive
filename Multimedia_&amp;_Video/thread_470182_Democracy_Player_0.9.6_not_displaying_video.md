---
title: "Democracy Player 0.9.6 not displaying video"
date: 2007-06-10
forum: Multimedia &amp; Video
---

### Post by samichx on 2007-06-10
After finally getting my hands on the New Democracy Player, the one with all of the features that I love on Feisty Fawn (aka 7.04) there was a problem. Schreeeech! Wha? Ok.

The video would not play on it ant I tried to get things working, searched high and low for errors, but came up blank for a bit. here is my solution, then I will continue.

sudo apt-get install totem-xine 

(Yes, that will get rid of gstreamer, although it will get things up and running without hurting much.)

The problem according to the DPF users is the nomenclature between libxine1* (Ubuntu) and libxine* (DP). This isn't  problem, although it is reminiscent of the effort that I used to have to put into an operating system and it's software. Don't work hard, think hard.

---

### Post by samichx on 2007-06-11
Ok, so far this has worked for me. Although my friends have had a little trouble with my method and found a greater solution that comes straight from the DP bug site. Check out [https://develop.participatoryculture.org/trac/democracy/ticket/7489](https://develop.participatoryculture.org/trac/democracy/ticket/7489) for the fix from the makers of Democracy Player TV.

---

