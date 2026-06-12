---
title: "TV card configuration"
date: 2008-05-09
forum: Multimedia Software
---

### Post by wilq on 2008-05-09
Hi!
Recently I' ve put my hands on a TV card. Only thing I know about it is a bt848 chip and the tuner is Philips Fl1256. 
It is visible in the system - lspci shows it as 
02:07.0 Multimedia video controller: Brooktree Corporation Bt848 Video Capture (rev 12)
I have tried to configure it by passing options to the bttv module. Unfortunately since I don't know the manufacturer or model of the card I am unable to pass the correct "card=" parameter. As for "tuner=" I use 23 because I' ve found that it is correct for Philips Fl1256. When I try to run tvtime-scanner it searches through all frequencies and finds nothing, showing "no signal" all the time, although the antenna is connected and options set to PAL.
Any ideas?:confused:

Ok I have found out that the card is AverMedia TV Capture 98 so the card parameter should be set to 13. But still "no signal" in tvtime. I checked the card in other computer running Windows and it works well.

---

