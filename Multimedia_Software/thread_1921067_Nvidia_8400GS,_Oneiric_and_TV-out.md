---
title: "Nvidia 8400GS, Oneiric and TV-out"
date: 2012-02-06
forum: Multimedia Software
---

### Post by BlueAngel-CPT on 2012-02-06
Hi there everyone,

I was busy setting up a media centre machine over the weekend on an old PC of mine. It's a LGA775 P4 3.0Ghz HT, 2Gb RAM and an Asus Nvidia 8400GS graphics card. I installed Oneriric, sorted binary drivers for the graphics card, installed and set up XBMC, got the sound working via my DVD player's 5.1 system. At the moment the machine is attached to an old 17" CRT monitor for testing, as well as my secondary TV (oldish LG CRT TV). I've got the TV attached with an SVIDEO->SCART cable.

My first port of call was having the TV on and connected, hoping that via the Nvidia X Server config it would pick it up when I clicked on "detect displays". It doesn't. Then I found a guide online (admittedly for much older versions of Ubuntu) and I thought I'd manually configure xorg.conf. Again, no luck.

Is there anyone here who has had a similar setup, that can possibly help? Which files would you like me to post?

Any help on what I'm doing wrong would be greatly appreciated.

---

### Post by BlueAngel-CPT on 2012-02-21
As it turns out, it was the cable. For anyone in this position - some graphics cards have a 7-pin S-video output. This doesn't mean you need a 7-pin s-video to RCA converter. I was advised by the helpful assistant at the local electronics store that the 4 pin s-video cable will work, as the extra pins are for audio - the 4 main pins are for video.

---

