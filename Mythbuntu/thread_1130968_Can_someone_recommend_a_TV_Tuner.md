---
title: "Can someone recommend a TV Tuner?"
date: 2009-04-20
forum: Mythbuntu
---

### Post by diaperpie on 2009-04-20
Hey, can someone please recommend a TV Tuner card compatible with MythTV and under $50. Thanks in advance.

---

### Post by newlinux on 2009-04-20
you'll need to be more specific. What type of signal are you trying to tune (DVB-S, QAM, ATSC OTA, analog, etc...). What type of interface (PCI, PCIe...)?

---

### Post by diaperpie on 2009-04-20
> **newlinux said:**
> you'll need to be more specific. What type of signal are you trying to tune (DVB-S, QAM, ATSC OTA, analog, etc...). What type of interface (PCI, PCIe...)?

I think it's DVB-S. It's a regular TV with cable.(I'm not sure if that's what you mean) The interface is PCI. Sorry, I'm kinda new to all of this.

---

### Post by newlinux on 2009-04-20
No need to apologize. Just need more information to point you in the right direction. We were all new at some point. Are you in the U.S. or Europe, or... that will get us more specific. In the U.S. cable companies use QAM (digital) and NTSC (analog).

---

### Post by diaperpie on 2009-04-20
Oh, ok. I'm in the US so I guess I have QAM.

---

### Post by rhpot1991 on 2009-04-20
You still haven't specified SD or HD.

If you want HD I'd recommend the HDHR, it has 2 tuners sits directly on your network, and can capture any clear QAM (locals mainly):
[http://www.silicondust.com/products/hdhomerun](http://www.silicondust.com/products/hdhomerun)

For SD many people use the hauppauge pvr-xxx series, but these are no longer made, as analog is dead.  Hauppauge makes some dual band cards that you should have success with (google or check back here before you buy), but they generally don't work OOB as well as the pvr-xxx series.  It may be worth your time to check with your cable company and see if they have any plans to phase out the analog signal.  More information: [http://www.mythtv.org/wiki/Digital_Television](http://www.mythtv.org/wiki/Digital_Television)

---

### Post by diaperpie on 2009-04-20
I have a SD TV. I was looking at the Hauppauge WinTV HVR-1250.
[http://www.hauppauge.com/site/products/data_hvr1250.html](http://www.hauppauge.com/site/products/data_hvr1250.html)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815116028](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116028)

Will this work with my TV? Or is it strictly HD? Will this work well with Mythbuntu?

---

### Post by AboveTheLogic on 2009-04-22
BTW, DVB-S is satellite, and in the USA only Dish Network uses it. DirecTV uses DSS, over the air antenna is ATSC, and as newlinux said, cable is QAM or NTSC.

> **diaperpie said:**
> I have a SD TV. I was looking at the Hauppauge WinTV HVR-1250.
[http://www.hauppauge.com/site/products/data_hvr1250.html](http://www.hauppauge.com/site/products/data_hvr1250.html)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815116028](http://www.newegg.com/Product/Product.aspx?Item=N82E16815116028)

Will this work with my TV? Or is it strictly HD? Will this work well with Mythbuntu?

the card itself supports NTSC (analog, SD only) and QAM (digital, typically HD)

the mythTV wiki says its currently only supported for digital use:
[http://mythtv.org/wiki/Hauppauge_HVR-1250](http://mythtv.org/wiki/Hauppauge_HVR-1250)

if you are using cable, you probably would be better off finding a card that is supported for digital and analog

poke around on the wiki if you have time, and see if you can find anything available, that's what I did before settling on my tuner (which wouldn't be ideal for you, its ATSC/NTSC only, no QAM)

---

### Post by mega30000 on 2009-04-23
I am just starting out with mythbuntu.  I know that the original post was for a $50 card.  But I wanted to add some feedback that after days of reading posts on how to get the "stock" hauppage card that came with my HP computer to work - I took someone's advice and just bought an HD SiliconDust tuner.  

While I did look at it from my windows pc (blasphemy- I know)to see if it was hooked to the network - I installed the firmware upgrades from their website.

Less than 15 mins later I had a tv signal on my mytbuntu pc and have not had a single problem.

---

