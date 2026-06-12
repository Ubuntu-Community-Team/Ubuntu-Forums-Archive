---
title: "Pinnacle 300i Analog"
date: 2006-12-19
forum: Multimedia &amp; Video
---

### Post by DrMega on 2006-12-19
Hi all

I have a Pinnacle 300i DVB + PAL tuner in my Ubuntu Dapper box. The device manager lists it, tvtime will scan it but I always get 'no signal'. I've followed numerous articles about similar cards but everyone else seems to get theirs working but I can't. Here's what I'm trying to do:

I'm trying to get the analog tuner working under Ubuntu. I have no interest at this stage in the DVB side of it.

Here's what I know:
1. That the card works fine and can receive a signal under Windows XP
2. Ubuntu recognises the make and model of the card without me having to do anything
3. The V4L driver apparently supports it (it is listed in the supported cards list)

Here's what I don't know:
1. Whether the default tuner is the PAL one or the DVB one (both exist on the same card)
2. HOW TO MAKE IT WORK](*,) :confused: 

I've read that I have to specify a card number and a tuner number, so I've tried creating a modprobe.conf file with card no 50 and tuner 33 (which I got from the V4L wiki site), rebooted and rescanned channels. All to no avail.

If anyone knows how to make this card work, please tell me because I'm starting to go insane with frustration at this point:mad:

---

### Post by DrMega on 2007-02-26
Come on guys, I know someone has had it working. It works fine in Windows and is the last hurdle in my media centre build. Any help would be appreciated.

---

