---
title: "MythTV"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by guernicaaa on 2007-05-22
I'm a little confused on this application.  I have a Phillips TV tuner card, and all I want to do is use it to hook up my Xbox and record some Halo clips onto my PC.  Now, what's the deal with the front end/back end stuff.  Can I install it and use it on just one PC?  Just hook the video out of my TV up to the video in of my TV card and record?

---

### Post by tgm4883 on 2007-05-22
Setting aside the fact that you didn't do the least bit of searching, Mythtv is more than you need.  First things first, you need to get the card working in linux.  It is a tv tuner, but does it also have video in, as that would be easier to hookup (straight from the xbox to the computer).  Once that is setup you can just record the video coming in without a problem.  Assuming that you either have a powerful enough computer or a Hardware encoder card.

---

### Post by guernicaaa on 2007-05-22
> **tgm4883 said:**
> Setting aside the fact that you didn't do the least bit of searching, Mythtv is more than you need.  First things first, you need to get the card working in linux.  It is a tv tuner, but does it also have video in, as that would be easier to hookup (straight from the xbox to the computer).  Once that is setup you can just record the video coming in without a problem.  Assuming that you either have a powerful enough computer or a Hardware encoder card.

Well, I just wasn't sure if I needed two separate computers to run it.  I have an AMD Athlon 64 3200+ with 2 gigs of ram.  I'm not sure if the card has a hardware encoder, but it does have a video input (along with a coaxial) 
So, I can run this on one PC then?  Would I install the MythTV front end or just regular MythTV?  What do I put in for all the database fields?

---

### Post by tgm4883 on 2007-05-22
go here and follow the guide that describes your situation.  You need both a frontend and a backend (they can be on the same computer) and mysql is setup for you.

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by reclusivemonkey on 2007-05-23
Installing MythTV just to record some video is complete overkill. You can record using either mplayer/mencoder or xawtv.

---

### Post by guernicaaa on 2007-05-23
Okay I installed mplayer, how would I got about recording from my tv card?

---

### Post by reclusivemonkey on 2007-05-23
The MPlayer documentation has plenty of information on what it is capable of;

[http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html)

---

### Post by fenian on 2007-05-23
Try ths...

> cat /dev/video0 > ~/Desktop/test.mpg

---

