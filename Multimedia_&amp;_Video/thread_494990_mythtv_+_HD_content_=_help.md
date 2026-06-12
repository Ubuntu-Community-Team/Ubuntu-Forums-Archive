---
title: "mythtv + HD content = help"
date: 2007-07-07
forum: Multimedia &amp; Video
---

### Post by hansoffate on 2007-07-07
Hi guys,

    I am about to make another backend/frontend for a new tv that I have been debating on buying.  Its a 32" LCD HDTV from VIZIO for 400 dollars.  If anyone knows anything about this model, I would like some input.  Anyways,  I want to build an HD recording mythtv box.

[https://secure.newegg.com/NewVersion/WishList/MySavedWishDetail.asp?ID=6115806](https://secure.newegg.com/NewVersion/WishList/MySavedWishDetail.asp?ID=6115806)
Also, a 500 GB hard drive at fry's for 90 bucks.
All of that, plus an pcHDTV-5500, will put me at  $560 everything shipped.  Which seems pretty decent for a good looking HD media center.

Of course, I will be spreading all this buying over the course of about 3 months, but hey, it will eventually be built.

Is there anything I should know about the pcHDTV-5500 series?  Are there any other cards that are as good.  How would I set this up with comcast?  Supposedly I get a special "HDTV" box which they send.  Now, does that mean I would have to make a channel changing script to change that box?  I really hated figuring out which code blasted my SAT STB, and the reason why I was moving to cable, is so I wouldn't have to fool around with that any more.

Anyways, thanks for the help,
Hans

---

### Post by PilotJLR on 2007-07-07
These HDTV tuner cards are designed for over-the-air terrestrial reception, not using cable input. What you would normally do is attach an HD anteanna, and it will tune over the air broadcasts. Works extremely well too!!

What you basically need is a capture card (not a tuner) that works with Linux and supports component or DVI input. I can tell you now... DVI input cards are unbelievably expensive. Not sure about component input, so that is worth at least searching for.

Personally - I juse use SD content from a satellite and get HDTV over the air. Of course, channels like HBO are obviously not over the air.

---

### Post by hansoffate on 2007-07-07
So, I what should i do?  Get a  PVR-500 and a pc-5500 for OTA?  Don't I need an antenna?  Should I just not get a pc5500 and try firewire input?

Thanks for the help,
Hans

---

### Post by williammanda on 2007-07-07
I currently use the pcHDTV-5500 as one of my HDTV tuner cards with comcast to receive HDTV channels. I get the basic service from comcast which they advertise as only SDTV but I get all the network HD channels (Fox, NBC, etc...). My understanding is that cable providers are suppose to provide the HD network channels for free but I don't think that is enforced. Comcast isn't very good about identifying the HD channels, so you will have to watch the channel to figure out which one it is. You will need to manually load the cx88_dvb module initially. I also use the FusionHDTV5 RT Gold card. It works equally well and doesn't need the cx88_dvb module loaded. It is taken care of already in linux. 
Thanks

---

### Post by newlinux on 2007-07-07
I have used a fusion 5RT Lite, Kworld ATSC 110, Avermedia A180, and a pchdtv 5500 for QAM (digital tuning of cable channels) for my cable HDTV and all work well. How many stations you will get unencrypted will depend on your provider as already stated. It varies from region to region as well. All of the cards above (except for the A180) can also tune analog cable (NTSC) however they are not hardware encoding like the PVR-150. I prefer the Kworld as it can be had pretty cheap and does ATSC/QAM/NTSC. 

If you want to record HD directly from a cable box you can use mythtv and firewire (without any tv tuner card) but you will only be able to get stations which have DTCP turned off. This varies from region to region as well.

---

### Post by underfunded on 2007-07-08
Hi All,

I too have a PVR-150 and a pcHDTV HD-5500 in my Myth box with Comcast HD cable box.  I would like to watch the live TV through the HD 5500 and record using the PVR-150.  My end goal would be to tune the HD 5500 to channel 3 or 4 and use my Cable box for changing channels.  I've been told that this is possible, but I don't seem to know how to make it happen.  Any help would be great.

UF

---

