---
title: "Asus P7131 dual tv-tuner, no channels found?"
date: 2011-06-23
forum: Multimedia Software
---

### Post by fireflite on 2011-06-23
Hi, i'm trying to get mythtv to work with my Asus P7131 Dual/hybrid tv-tuner.

I'm running Ubuntu "natty", and mythtv 0.24.1

My problem is, that the tv-tuner works fine in "Tv-time" and "Xawtv", where i can scan the channels and find both dvb-t & analog channels.
Thats is just great, so apparently the card is working ;)

Unfortunately, i have this problem in the Mythtv 0.24.1 backend:

The card is found in mythtv, with all the correct parameters (probed info), but when i add the tuner to mythbuntu's backend, and scan for channels, i get the message "No channels found", no matter what type of card i add :(
I tried with and without grabber, but to no avail :(

I tried to add only the analog tuner, but get the message :
"no channels found"

I tried to add only the digital dvb-t tuner, but get the message:
"No channels found"

I then wiped the natty, and installed the version from mythbuntu, but i run into same problem

does anyone experience the samme problem in mythtv ?

Regards
Fireflite

---

### Post by then_dude on 2012-05-05
i have the same problem  does anyone has a solution to the problem ?   thanks

---

### Post by singedwings on 2012-05-18
I'm not trying to be patronising but have you checked out the mythtv wiki to see if there are any special instructions for you card? [http://www.mythtv.org/wiki/Category:Hardware]("http://www.mythtv.org/wiki/Category:Hardware")

What chipset does the card use? Post your ```
lspci
```

---

### Post by kenzu on 2012-05-22
try to raise the scanning timeout to 3 times normal. That fixes it for me ;-)

---

