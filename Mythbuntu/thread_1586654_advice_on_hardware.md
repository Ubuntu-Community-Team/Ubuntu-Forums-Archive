---
title: "advice on hardware"
date: 2010-10-02
forum: Mythbuntu
---

### Post by benlyboy on 2010-10-02
This I guess is not really a myth question but here goes

I am getting ready to build a new frontend only system. I want to use it to replace my current frontend/backendend unit in my living room. The old system is a little to noisy and a little to big as well. the old unit will be moved and become the backend.

I have a Asus p5n7a-vm motherboard that I plan to use.

Now this is where I would like to get some feedback I am thinking of not using a hard dive as such but instead using a Addonics ADSAHDCF CF - SATA HDD Adapter and a card.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812174005&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-Adapters+and+gender+changers-_-Addonics+Technologies-_-12174005]("http://www.newegg.com/Product/Product.aspx?Item=N82E16812174005&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-Adapters+and+gender+changers-_-Addonics+Technologies-_-12174005")

Also could tis be used as the power supple? 
 [http://www.newegg.com/Product/Product.aspx?Item=N82E16817129006]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817129006")

Both would cut down on noise, and as I am thinking of building my own case it might even make for a smaller foot print, but to be honest I have no idea if these parts will work together.

---

### Post by ian dobson on 2010-10-02
Hi,

I'm using a CF - SATA adapter on my frontend for the last 18months now without any major problems. Just setup the fstab so that writes to the card are reduced (noatime is the biggest).

You'll need atleat a 4Gb card (I would recommend a fast 8Gb card). To reduce the load on the CPU then maybe look at getting a NVidia graphic card (9300 or better). My frontend is an underclocked (1200MHz) e5200 and it can playback any video I throw at it (1080p,mkv,264h HD) without breaking into a sweat (CPU fan runs at 400-500rpm) and is almost silent.

Regards
Ian Dobson

---

### Post by LowSky on 2010-10-02
that power supply only puts out 85 watts. unless you plan on using a microITX VIA or intel atom motherboard forget it. think it through that asus board will be using at least a 65 watt prossesor then add the mothboards graphics plus any other stuff like optial drives. find one that puts out at least 150 or 200.

---

### Post by benlyboy on 2010-10-02
OK so yes to the card no to the power supply.

Ian any reason not to use the boards on board video? 
My plan was to use the on board NVIDIA GeForce 9300

lowSky you are right I should have looked a little closer and thought it through.

Any ideas in a good silent or near silent power supply?

thanks guys for the input

---

### Post by ian dobson on 2010-10-02
> **benlyboy said:**
> OK so yes to the card no to the power supply.

Ian any reason not to use the boards on board video? 
My plan was to use the on board NVIDIA GeForce 9300

lowSky you are right I should have looked a little closer and thought it through.

Any ideas in a good silent or near silent power supply?

thanks guys for the input

OK, if the onboard graphic is a 9300 and it supports vdpau then there shouldn't be any reason not to use it. 

Regards
Ian Dobson

---

### Post by benlyboy on 2010-10-02
OK thanks Ian 

As you have been using a CF - SATA adapter, can you tell me how hard it is to install and set up?

---

### Post by ian dobson on 2010-10-02
Hi,

I actual started using a normal laptop harddisk in my frontend for a while, but it was too loud so I just copied (using dd) from the harddisk to the CF card.

If the CF card/adapter looks to the BIOS like a normal harddisk, then just install mythbuntu normally. When your finished and the system boots ok, edit the /etc/fstab file and add the option noatime (this reduces the number of writes to the card see [http://kerneltrap.org/node/14148](http://kerneltrap.org/node/14148))

I've been running now with a CF card for about 14months and have had no problems with in, and the frontend boots really fast (11second fron grub to Mythfrontend).

Regards
Ian Dobson

---

### Post by benlyboy on 2010-10-03
Thanks Ian


Sounds ok.

 When I get it built, I will post if I run into any problems

---

