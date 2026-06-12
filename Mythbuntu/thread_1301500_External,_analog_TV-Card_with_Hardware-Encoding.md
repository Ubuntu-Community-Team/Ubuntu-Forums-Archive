---
title: "External, analog TV-Card with Hardware-Encoding"
date: 2009-10-26
forum: Mythbuntu
---

### Post by pz.daniel on 2009-10-26
Hello world ;-)


As the titel already tells:
I'm looking for an external, analog TV-Card with Hardware-Encoding that works together with Mythbuntu.

What I want to do:
I want to install an Home-Entertainment-System. As we have more Ubuntu PCs/Laptops than Windows, I decided to try this system getting work with Mythbuntu.
The Server could possible be the [ASRock ION 330]("http://www.amazon.de/gp/product/B002BZBTS4/ref=s9_k2a_gw_tr02?pf_rd_m=A3JWKAKR8XB7XF&pf_rd_s=center-2&pf_rd_r=1GT1K8T6S4BF4R5KVFMG&pf_rd_t=101&pf_rd_p=463375173&pf_rd_i=301128").
This one should play 1080 HDTV (like .mkv, h264, ...) and doesn't need too much energy ;-)
The problem is just the TV-Card. The Nettop doesn't have any additional PCI-slot for an TV-Card, thus I need an external one :-(


Does anybody know such an TV-Card that is cheap and works with Mythbuntu?




Thanks for any reply!
Greetings from Germany,
Daniel




PS: The TV-Card has to work with European-TV ;-)

---

### Post by joshoekstra on 2009-10-26
A Hauppauge HVR-900? dunno how good support for that is...
A Terratec Cinergy HTC USB XS HD?
Asus My Cinema-U3000Hybrid?
Avermedia Avertv Hybrid Volar HX
You&#314;l have to look up support on linuxtv.org but these seem to be the cheapest options with more or less the same features...

---

### Post by pz.daniel on 2009-10-26
Thanks for your reply!

I looked up  the cards, but I think that all of them are just software-encoders.
Avermedia says, that they have lizensed the best software encoder...so the encoding is done on the pc, isn't it?!
If I use the ASRock Ion 330 I'm afraid that it hasn't enough power to record and play files at the same time (especially if the tv-card records and you wanna watch HD-movies).

I think the Hauppauge WinTV-HVR-1900 is one of those cards I'm looking for. Hardware-Encoding, External (USB), Analog-TV, ... but sadly no HDTV xD ... AND it should be Linux-supported (it is written on linuxtv.org <-- thanks for the hint).
If no one knows a cheaper/better one, I'll try this one...

---

### Post by dddw on 2010-12-17
ha great post!
I have a asrock ion330 and was looking for the perfect tvcard...
any followup on this post? did you buy the card? and is it as good as it seems?

---

### Post by pz.daniel on 2010-12-17
Hey dddw,

do you know how old this thread is? ;-)

Well, in the end I bought the Hauppauge WinTV-HVR-1900 - a year and some months ago :-D

At the beginning I had a lot of problems to get the whole system working, cause my tv had only 720p with cut off (some pixels are missing on the edges...) and to get the card working was also really difficult. But with the new versions of mythbuntu the support of the card was getting better and better, and today it works out of the box.
(But after some startups I can't use the card...I think thats the problem of mythbuntu...error:"all cards are busy")

However, I won't give you the advise to buy the card...unless you know the following.
The picture of non-HD cards is terrible. I tried the card with windows and the included as well as the latest drivers from the hauppage site...but the picture was even worse.
The card can't compete with the integrated tuner in my tv.
It's like watching youtube videos with 480p on an 720p tv (I think, the native resolution of that card is something around 480p? But I actually don't know...I could be wrong here ;-) ).

Oh, and before I forget that:
The asrock ion 330 or any device close to that is NOT able to play 1080p properly. Even with the ion-chip and VDPAU it doesn't work fluently. At high-bit-scenes (for example fire, explosion, (water), action (fast cuts, fast scenes), it keeps on lagging...not really bad, but lagging.
Please note that this is my experience, it could be different on a 1080p tv (no downscaling, so it might work there).


hope, that'll help you a bit?!

Greets,
Daniel



PS: sry for my english, it's too late here :-D

---

### Post by bcg30506 on 2010-12-21
I just got a Hauppauge HVR-1950 today and it is working great on my mythbuntu 10.04 system with MythTV 0.23.1-fixes.  The only thing I had to do other than download the firmware file and put it into /lib/firmware was to upgrade my kernel to 2.6.35-22-generic-pae using synaptic then reboot.  All is well.  I have an NVIDIA video card and VDPAU works perfectly.  I only use the analog cable inputs with this and do not use the remote control since my old PVR-150 handles that.

---

