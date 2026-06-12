---
title: "Impossible Tv Tuner Card"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by cPhoX on 2007-11-28
Hi
I have had limited experience with linux, but i have learnt alot by seeking my many answers in these forums. Ive come across a problem however that I cant find answered anywhere. Ive been looking for days. So Ive signed up today to get some specific expert help.

I have a tv tuner card that is a ST_Labs Pal B/G D/K with FM Tuner. It has worked previously very well under windows. 

TVTime opens and closes immediately telling me " No XVIDEO port found which supports YUY2 images", 

Xawtv turns my screen black and I have to ctrl-alt-f2 and then ctrl-alt-f7 to get my display back. kdetv doesnt work either.

The system recognises the card's chipset as being philiips semiconductors etc.....

Ive tried a few card numbers and updated them by opening  /etc/modprobe.d/options and adding the line "options saa7134 card=X tuner=Y" where X and Y respectively are the card and tuner numbers i try

my computer does not have the documentation with tuner card numbers that alot of websites refer to.

Ive been working on this system for ages now, with my goal to have all hardware working with it. My ATI X1300 was a challenge, my SB Live 5.1 was also a challenge but this tv tuner card is above me. Please Please Help

---

### Post by josesanders on 2007-11-30
I would just keep trying different card numbers.  I've found that the tuner number doesn't matter.  Just try the following:

$ sudo rmmod saa7134-alsa
$ sudo rmmod saa7134
$ sudo modprobe saa7134 card=<card number>

Then open TVTime and see if you can tune in channels.  Make sure that you try different inputs.  For me, I found that about 30% or so of the card numbers worked, but maybe that won't be the case for you.

There are scripts out there to automate this, and they should be pretty easy to find.

---

### Post by Turin Turambar on 2007-11-30
We have a cable tv network. I managed to scan for channels... but no signal? 
What does that mean? There are also many PAL versions to choose... I really don't know which to pick.

---

### Post by PhilJ on 2007-12-11
Hi ,
  Serbian tv is PAL/B-G


phil

---

### Post by Turin Turambar on 2007-12-17
Thanks! :)
No signal meant that I didn't use the right kernel driver for my card. 
Tvtime found all channels by itself, but I set PAL B/G for sound.

---

