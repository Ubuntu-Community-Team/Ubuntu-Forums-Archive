---
title: "Linux HDTV tuner card?"
date: 2006-03-02
forum: Multimedia &amp; Video
---

### Post by samwh on 2006-03-02
Does anyone know of a good PCI HDTV tuner card, with hardware decoding, i1080, compatable with American signals, and can capture other HDTV input? I t has to be able to access broadcast signals directly, and be compatable with Linux (duh).

I already looked around, Avermedia has a good, cheap, one but they dont have any plans to get Linux HDTV support. All of hauppages HDTV cards are European, and the I dont know if the PCHDTV ( the linux only ones) can get i1080 (plus they don't have hardware decoding.

ANY links, product info, or whatever would be great (gotta get that MythTV box running :))

Thanks guys!

---

### Post by luna6 on 2006-03-02
Just letting you know there is no hardware decoding involved because the HDTV card just downloads the stream of data/bits. Dvico Fusion HDTV works nicely as well.

---

### Post by samwh on 2006-03-02
But HDTV/digital tv is compressed right? Shouldn't there be a hardware decoder for this?

---

### Post by luna6 on 2006-03-02
The capture card is like an AM/FM tuner card, just download the bits, your video card will then process that information, so for like cpu usage the video card is relevant. The nvdia cards from maybe 5200 and up have a nice decoder but I dont believe its available in their linux drivers (which sucks), and ati seems to have some good stuff after the um 1200 or something like that. I watch a lot of hdtv and basically if your cpu is 2.0 ghz or higher and you have a decent video card the video quality is fine. Your location relative to the hdtv towers makes a big difference, if you dont get a strong signal then you will see a lot of pauses which will drive you nuts.

---

### Post by samwh on 2006-03-02
Oh, neat. I hope Nvidia comes out with drivers for the decoder soon. I have a AMD athlon XP 3000+, so I should be fine...but If anyone knows of any stand alone decoders, great. What codec is it? Mpeg-4?

And anyone know of any good Linux HDTV tuners that have the specs I outlined above (without the hardware decoding :)). Maybe <100 bucks?

---

### Post by bumpusth on 2006-03-02
Do you need 8VSB or QAM64 or QAM256 decoding?

[http://www.linuxtv.org/wiki/index.php/ATSC_cards](http://www.linuxtv.org/wiki/index.php/ATSC_cards)

---

### Post by samwh on 2006-03-02
Er... I dont know... I thought there was a standard for HDTV? I live in Ohio, which one would that area use?

---

### Post by bumpusth on 2006-03-03
Well, there is the way their encode the stations into the frequency bands which is different if you are trying to get OTA or from your cable company.

OTA is 8VSB in the US. Pretty much every card covers this type of HDTV transmission.

If you are trying to hook your Time Warner/Comcast/Adelphia/Whatever (northeastern US person here) then you are probably going to need a card which does QAM decoding. Now there are two kinds 64 and 256. Getting a card with 256 means that you should be compatible with your cable company (I believe cards that do 256 also do 64 even if they don't state it on the box).

---

### Post by mabhatter on 2006-03-03
OMG!!
I'm surprised nobody has posted this yet but go here[http://www.pchdtv.com/]("http://www.pchdtv.com/") for Fully Linux compatible HDTV tuners!!!   I haven't bought one yet, but they look pretty cool.  Note: they support ONLY Linux!!! but they Open almost all their stuff.

---

### Post by reet on 2006-03-03
The pcHDTV card is mentioned in the [previous link]("http://www.linuxtv.org/wiki/index.php/ATSC_cards").

---

### Post by bill343 on 2007-10-23
I just got this card, the Pinnacle PCTV HD Card, from WOOT. I am tryign to see if there are drivers for it for the new Ubuntus distro. Any body used this card before?

---

### Post by twizler on 2007-11-11
YOU NEED TO GO HERE ! -- 
PCTV HD Pro Stick-- and others 

pinnacle usb tv tuner
> 
[http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)

HAS AN AWESOME HOW TO !!!

---

### Post by sloggerkhan on 2007-11-11
I've been thinking of getting an hdHomeRun. [http://www.silicondust.com/wiki/products/hdhomerun](http://www.silicondust.com/wiki/products/hdhomerun)

It's not exactly a tuner card (better, IMO). Of course, I 'd be using it with a laptop if I got it.

---

