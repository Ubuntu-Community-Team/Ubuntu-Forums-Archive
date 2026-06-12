---
title: "Myth TV: What Kind of Horsepower do you need?"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by cody50 on 2007-05-15
I'm am looking to set up a MythTV box running feisty. currently I have a Pentium III 1 ghz old dell with 512 mb ram and an nVidia Geforce 2 card. 

What would you recommend as far has computing power for running mythTV? would my old computer be able to handle it? I am envisioning it as a Front end and Backend. It would be dedicated to just this task.

thanks for the input.

---

### Post by tgm4883 on 2007-05-15
You wouldn't be able to do HD, but if you got a tv tuner with a hardware encoder (something like the PVR-150 or the PVR-500 if you prefer a dual tuner) then you should be fine.

---

### Post by newlinux on 2007-05-15
If you are talking SDTV - then your pentium III has enough power, especially if you get a hardware encoding card (pvr-150, pvr-250, pvr-350, pvr-500). The pvr-350 also has hardware decoding via tv-out to further take load off your processor.

for more info on hardware requirements:

[http://www.mythtv.org/docs/mythtv-HOWTO-3.html](http://www.mythtv.org/docs/mythtv-HOWTO-3.html)

---

### Post by cody50 on 2007-05-15
yeah I don't think HD is too big of a problem for now, especially if i can make due without buying alot of new equipment. 

As for tuner cards, is that how it works? you want one that can do encoding on the card itself so the cpu does less?

and on that page this caught my eye
> A PIII/800MHz system with 512MB RAM can encode one video stream using the RTjpeg codec with 480x480 capture resolution and play it back simultaneously, thereby allowing live TV watching.

---

### Post by newlinux on 2007-05-15
> **cody50 said:**
> yeah I don't think HD is too big of a problem for now, especially if i can make due without buying alot of new equipment. 

As for tuner cards, is that how it works? you want one that can do encoding on the card itself so the cpu does less?

and on that page this caught my eye

Yep... you'll have no problems power wise if you use a hardware encoder. But even without a hardware encoder your system *should* be powerful enough - but since yours is close to the low end for live tv playback I'd recommend a hardware encoder so you don't have to do any performance tweaking to get it working.

---

### Post by tgm4883 on 2007-05-15
Go with a hardware encoder.  You will be much happier with it.

---

### Post by cody50 on 2007-05-15
So the difference between [this 70 dollar card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815116625") and [this 30 dollar card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814122221") would be the hardware encoding capability?

A friend of mine said he has an ati tuner, so I think i'll try it with that just for the hell of it and then if that doesnt work i'll have to buy a better one, maybe that pvr 150

---

### Post by newlinux on 2007-05-15
which ATI tuner? Many aren't supported in linux. And yes, hardware encoding is a major difference between the two cards.

---

### Post by cody50 on 2007-05-15
I'm not sure but he had it working with a simpler tv tuner program. I'm a little wary about buying the pvr-150. It looks like lots of people are getting that other one that is not linux compatible. at least thats what the reviews on newegg were saying.

---

### Post by newlinux on 2007-05-15
> **cody50 said:**
> I'm not sure but he had it working with a simpler tv tuner program. I'm a little wary about buying the pvr-150. It looks like lots of people are getting that other one that is not linux compatible. at least thats what the reviews on newegg were saying.

Oh yeah, I think they are getting the HVR-1600 or something... That sucks. Can always return it though or buy it in a store. Good luck with the ATI. If your friend has it working in linux, then you are probably fine.

---

### Post by tgm4883 on 2007-05-15
That was a problem a while back when they were short on the PVR-150 cards.  I do recommend the PVR-150

---

### Post by Kirurgs on 2007-05-16
Hey, it depends on what are you trying to do with that card: if just watching TV, it's no big deal, I did that on PIII 450 with 256 RAM with tvtime (bet I've found for that purpose), the thing is that TV uses video card overlay to display things directly into FB, which is HW and freakin fast...
If encoding, well that's can be tricky, though...

---

### Post by lonewolf_timberwolf on 2007-05-16
Personally I bought the Hauppage PVR-500, its essentially two PVR-150s in one card (dual tuners). So as I'm watching one channel I can record on another. It worked right out of the box :) Its almost twice the price of the card you were talking about, so if money is a major factor I'd go for the PVR-350. I haven't heard many complaints about it.

The only thing I would recommend would be to have two hdds if you get the PVR-500. One for the live recordings and one for the scheduled recordings, because even my Athlon 4800 X2 had a hell of a time trying to do both at once. When I added a second SATA drive, problems went away.

---

### Post by newlinux on 2007-05-16
> **lonewolf_timberwolf said:**
> Personally I bought the Hauppage PVR-500, its essentially two PVR-150s in one card (dual tuners). So as I'm watching one channel I can record on another. It worked right out of the box :) Its almost twice the price of the card you were talking about, so if money is a major factor I'd go for the PVR-350. I haven't heard many complaints about it.

The only thing I would recommend would be to have two hdds if you get the PVR-500. One for the live recordings and one for the scheduled recordings, because even my Athlon 4800 X2 had a hell of a time trying to do both at once. When I added a second SATA drive, problems went away.

That seems quite odd. sounds like a hard drive problem or something. Two of my frontend/backends have multiple digital and analog tuners with much less power than that, and on both of them can record mutltiple shows while watching a show -- digital (including hdtv) or analog (hardware encoding and not hardware encoding) -- and/or streaming a show across the network with one  hard drive, without any problems.

I have a pvr-150, but not a pvr-500 (which is essentially two pvr-150s on one board). That just doesn't seem right, and it definitely shouldn't be because processor power. That Athlon 4800 X2 is WAY more power than a hardware encoding tuner needs to run (or any non hardware encoding tuner).

Are you using mythtv?

---

### Post by cody50 on 2007-05-23
I know I'm just being paranoid, but if the system requirements for the [pvr-150]("http://www.hauppauge.com/pages/products/data_pvr150.html") say 1.2 ghz, and I only have my trusty 1ghz p3, is there anything to worry about?

---

### Post by tgm4883 on 2007-05-23
Think of that as a windows requirement

---

### Post by newlinux on 2007-05-24
> **tgm4883 said:**
> Think of that as a windows requirement

:)

---

### Post by cody50 on 2007-05-24
haha. thanks for the info. will be buying a pvr 150 for my mythbox most likely.

---

### Post by cody50 on 2007-05-30
Quick question about the PVR-150, It says it comes with a remote and a remote reciever cable. How do those work with the mythTV interface? do they work out of the box? if not is it not too hard to get them to work? I ask in this thread since it seems like some of you guys have this card.

---

### Post by tgm4883 on 2007-05-31
> **cody50 said:**
> Quick question about the PVR-150, It says it comes with a remote and a remote reciever cable. How do those work with the mythTV interface? do they work out of the box? if not is it not too hard to get them to work? I ask in this thread since it seems like some of you guys have this card.

Really easy to get working.  You have to install lirc

follow this guide
[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

---

