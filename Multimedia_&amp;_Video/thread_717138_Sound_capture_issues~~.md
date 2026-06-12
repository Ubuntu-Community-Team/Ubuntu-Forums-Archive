---
title: "Sound capture issues~~"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by drewcoon on 2008-03-06
I've been using Ubuntu for about six months, and I have to say that everything about this OS is awesome except for a few sound issues. Sound often can't be mixed from several sources (ie sound from a java applet and embedded flash at the same time), but I can live with that.

My problem is that none of my sound recording software works correctly regardless of how I alter the "sound capture" device settings in sound preferences. No matter what setting I put it on (unless on "silence" or "test sound", testing the input always gives the same message:

[img]http://i16.photobucket.com/albums/b23/Drewc2k5/Screenshot-gnome-sound-properties.png[/img]

has anyone else had a problem similar to this before? Here is a screenie of my various sound-related hardware wankery if it can be any help,

[img]http://i16.photobucket.com/albums/b23/Drewc2k5/Screenshot-DeviceManager.png[/img]

I have almost no knowledge of sound cards at all (I think sound might actually be onboard the motherboard on my comp, I've never opened it up besides to put in a wireless card). UPDATE - the sound card is in fact on a PCI bus, for the hardware information tells me so :)

Anyone have any ideas? Thanks in advance? :)

---

### Post by sonrock3 on 2008-03-07
Sound solution:
(Ubuntu-gusy gnome)

Hey, tell me about it!  After much experimentation with trying
"sound recorder"
+ playing embedded flashplayer item in webpage
+ bbc radio online that requires realplayer,
I've concluded from success

1)To play back Sound Recorder,
ensure sound not in use by any other application and then restart recorder
- this means close any webpages that were previously playing sound
+ close realplay

2) To fix flashplayer sound via Firfox:
install 9.0.48.0.2 +really0ubuntu12.2 (after ver ...12 installed)

Good luck!

Stephen

---

### Post by drewcoon on 2008-03-07
I don't think you understand my problem, my main problem is that I can't record any sound (ex, with a microphone) because I get errors while attempting to set up the sound capture part of my sound settings for some reason. Any sound editing program that has a record option either gives me an error or just crashes completely when I try to use that feature.

I've tried with only one program running, and I've tried killall esd (fixes most of my sound problems), but nothing helps.

---

