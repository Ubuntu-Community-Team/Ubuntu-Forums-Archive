---
title: "After installing libxine1-gnome, no stereo sound through SPDIF"
date: 2009-01-30
forum: Multimedia Software
---

### Post by Almarma on 2009-01-30
I have a strange problem with Ubuntu 8.10. I have installed right like older releases (I'm a Ubuntu user since 7.04) and I always managed to have SPDIF sound to work properly. I check "IEC958" in sound properties and configure properly SMPlayer and VLC. I also use Kaffeine for my DVB-T USB tuner. Well, with this setup, I get all sounds working in a external Onkyo decoder (optical SPDIF). The stereo sound works, and the AC3 and DTS sound works too, but in Ubuntu 8.10, just after installing, worked fine, but I didn't got original DVDs working in Kaffeine, so I tried Medibuntu repository and it didn't solve the problem, so after it, I installed libxine1-gnome package, to try to get AC3 sound in Kaffeine. Well, after installing it, the stereo and system sounds doesn't work anymore. Now, I get AC3 and DTS sound without problem (also in Kaffeine, who previously played everything in stereo). That's right. But when trying to play DVB-T stereo sound in Kaffeine, or MP3 music in Amarok, I get no sound at all. And this happens with all the applications I have installed. I have been investigating the comprehensive sound problems guide, but I still have no stereo sound. I don't know how to solve this without reinstalling Ubuntu again...

Any idea of a possible solution? My sound card is a Realtek ACL883 (Nvidia onboard chipset).

Thank you!

---

### Post by morganGDFP on 2009-02-09
Hey.
Unfortunately I don't have a solution to your problem.. I do, however, have exactly the same problem. 

For some strange reason I am unable to get stereo sound through the S/PDIF..

if I play a movie on VLC that is in surround sound it works perfect but if I try to play something that is in stereo I get nothing out through the optical..

I get audio through the headphone jack on the front of the PC though..


I can clearly remember that it did use to work earlier (with ubuntu 8.10) but at some point (probably after i updated ubuntu) it stopped playing stereo..

I suppose I could plug in an analog RCA cable in the amplifier as well and just use that for my music but I would prefer a more elegant solution..

Thank you!

---

### Post by Almarma on 2009-02-09
Hi Morgan,

Very interesting, so I'm not the only one with this problem. I thought my problem started after installing "libxine1-gnome" package, but your comment make me wonder if it is related with another update. Maybe a new kernel update...

I agree with you that the most "elegant" solution is to have this fully working like before. But sadly, I think this is difficult to be solved, because not many people is having this problem. Is very anoying to have no sound with Amarok, with DVB-T and with Youtube and another Flash video websites...

Maybe we should report a bug to Ubuntu developers...

---

### Post by morganGDFP on 2009-02-12
Hey.
**** it, I plugged the analog cable from my PC to my amp..It's far from perfect, I have to switch back and forth from digital input to analog on my amp but at least now I can listen to music again.

It appears as if it is the sound card (or driver or whatever) that decides that it should play surround sound through the SPDIF and everything else through the analog output..

Weird..

Btw I have a nVidia Corporation MCP67 High Definition Audio (rev a1) ( ALC888 ) sound device..It's one of those MCI mainboards with onboard audio MSI K9A2 something I think it's called..It's a relatively well used mainboard and I'm surprised no one else has this problem..

---

### Post by Almarma on 2009-02-20
Ok. I have discovered the most weird thing I have seen in Ubuntu yet: I have full sound thought digital output. Both, AC3 and stereo sound works, but stereo sound sounds EXTREMELY LOW!!! That's my problem now. I have discovered it today. How can I make the general sound much much louder? AC3 sound works right, because it's totally digital, and is passed to the external amplifier, and this amplifier manages the volume. But the stereo sound is processed by the Ubuntu drivers. I have to put my Onkyo amplifier volume at max to hear it relatively well, but this is totally insane. If I forgot to low it when I change to play a movie, I can broke the windows of the living room!!! Put this amplifier to max. volume is totally insane!!!

Any idea on how to do it? The Ubuntu volume controls are all at 100% already.

---

