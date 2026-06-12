---
title: "m-audio transit USB audio and edgy (or alternatives)"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by pHz on 2007-01-14
im in the middle of moving to linux for audio work (committed hobbyist) because im not happy about the prospect of vista but mainly to support long-time acquaintance jorgen aase in the development of his cross platform sequencer project energyXT2

right now i have onboard sound (sigmatel AC97) working fine on my laptop but the quality obviously isnt great - i do have a high end firewire audio interface (mackie onyx satellite) but for my relative noobness freebob looks a bit much to take on at the minute

in the meantime im in the market for a relatively cheap USB interface to tide me over and the m-audio transit looks relatively good

so my question - anyone using the transit under ubuntu 6-10 ? - and if so does it still need the manual firmware loading each time you plug it in ?

follow up question - any other affordable USB audio interfaces that work out of the box or with one-time only setup processes ?

thanks in advance

slainte :confused: rob

---

### Post by pHz on 2007-01-15
erm - bump

slainte :oops: rob

---

### Post by mkoyle on 2007-05-23
There are a lot of USB devices supported by ALSA drivers (it is the USB-audio driver).  Once you have a device supported by the driver ... as long as is isn't a firmware loads from the system at bootup (i.e. Tascam US-122), it is a cinch.  

If you happen to already have the Tascam, it is possible to use it with Ubuntu, but you will have to find some help-- I haven't gotten that done, yet.  There are tutorials around and there is no question it works.

There are three soundcards listed at [http://alsa.opensrc.org/Alsa_Preferred_Soundcards](http://alsa.opensrc.org/Alsa_Preferred_Soundcards) that fit what you are looking for: USB Soundblaster Audigy 2 NX, Quattro USB audio interface, Terratec Aureon 5.1 USB (including the MK2), Uno USB MIDI interface (with the firmware thing the Tascam needs), the Tascam USB devices.  If you come across anything else, just search for it and snd-usb-audio or Ubuntu and see if anyone says it works.  The [www.alsa-project.org](www.alsa-project.org) website is a great resource to verify ALSA support.

I have a Edirol UA-700 that works rather well, too.  They are rather scarce, but if you can find one on eBay, it shouldn't go for too much (even though they were $1000 devices five years ago-- LOL how technology changes).

--Matthew

---

### Post by mkoyle on 2007-05-23
About the transit: talk to mpvano; he seems to think it is great (and easy in Ubuntu):

[http://ubuntuforums.org/showthread.php?t=80540](http://ubuntuforums.org/showthread.php?t=80540)

--Matthew

---

