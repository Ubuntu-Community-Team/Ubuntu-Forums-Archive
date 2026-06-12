---
title: "Video card recommendations"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by DapperMe17 on 2006-12-01
I have an old p3, 600mhz with a stock, old nvidia riva tnt vanta that I suspect could be defective, as my Xubuntu is showing up way too large for the monitor size (even though I have the nvidia legacy glx driver installed).


I'd like to spend less than $50 (maybe GeForce 5500 from local electronics store). I'd like to make sure that it will be recognized by Xubuntu out-of-the-box.


Thanks for any input!

---

### Post by Shatrat on 2006-12-01
I think support will likely not be a problem.
You should find out if you have an AGP 4x or 8x or only PCI expansion slots available.

With something that old, I would just try and score something on ebay or from a friend or something used.  Detection shouldnt be a problem, within reason driver availability is better for older cards than for brand new ones.

---

### Post by DapperMe17 on 2006-12-01
The current card is a 8mb version, and says it's AGP 2x upgradeable. I assume that means I can move up to 4 or 8.


With a P3 and 384mb ram max...should I stay with a simpler video card...say, one with 64 to 128mb memory....vs 256+?

---

### Post by DapperMe17 on 2006-12-02
Anyone else?

---

### Post by JAW on 2006-12-02
No offense but with somthing that old i'd stick with a budget model card like the GeForce MX400, the AGP rates supported by chipsets were flaky on those old systems, although they say they support x4 or x8 AGP quite often they wouldn't. I fear if you buy even a semi-decent modern card, it will be gimped by the motherboards chipset...

---

### Post by DapperMe17 on 2006-12-02
Jaw,

Thanks for your valuable input. I would agree.

I noticed an mx400 on NewEgg.

Thanks for your $.02:-D

---

### Post by DapperMe17 on 2006-12-02
My choices are...

Geforce mx400
Geforce mx440
Geforce mx4000


What is the best performing card for video (of the three)?

---

### Post by DapperMe17 on 2006-12-02
Anyone care to offer a card choice???

---

### Post by Talon2 on 2006-12-03
I've got a old an old P3 750.  Many mobos from this time only supported AGP 2x.  Mine only supports 2x.  2x means the mobo only provides 3.3 volt juice.  Any AGP card you put in this system has to be able to run on 3.3 volts.  Therefore you are limited to cards that support AGP 2x.  You have to research this very carefully.  Here are a couple of examples that do:

GeForce MX4000 - [http://www.newegg.com/Product/Product.asp?Item=N82E16814127128](http://www.newegg.com/Product/Product.asp?Item=N82E16814127128)

ATI 9250 - [http://www.newegg.com/Product/Product.asp?Item=N82E16814127148](http://www.newegg.com/Product/Product.asp?Item=N82E16814127148)

---

### Post by Scunizi on 2006-12-03
I've got both the MX400 & 440 running for the last couple of years (or longer) in different machines on my network at home and they proven to be stable and quick relatively speaking.  You're not going to do any present day 3d stuff with them, some maybe.  But for general computing go for it.

---

### Post by DapperMe17 on 2006-12-03
Thanks guys, or gals!

Talon, the manufacturer data for the video card says it indeed is 2x...but lists "upgradeable after it. I would assume that means something up from there. 

Thanks for your link too!
Looks like a winner.

---

### Post by Talon2 on 2006-12-03
> **DapperMe17 said:**
> Thanks guys, or gals!

Talon, the manufacturer data for the video card says it indeed is 2x...but lists "upgradeable after it. I would assume that means something up from there. 

Thanks for your link too!
Looks like a winner.

I didn't see "upgradable" so I'm not sure what to say.  What I know is that you must be careful to ensure that any AGP video card you choose supports the same level of AGP that your mobo does.  It is possible to fry things.

One thing to consider:

The ATI 9250 card will work with 3D cability with the open source radeon driver included in Ubuntu whereas the Nvidia based card needs the Nvidia binary driver to be installed at some point after installation.

Both of these cards benchmark close to the same.

I'm using a ATI 9250 on the system I'm using right now.  I'm still using Dapper because something related to 3d is borked in Edgy.  There are already bugs filed and I hope the problems are fixed before the next release.  You might want to stick with Dapper until the next release.

Good luck.

---

