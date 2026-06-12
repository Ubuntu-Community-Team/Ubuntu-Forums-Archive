---
title: "best recommended Tv Tuner card for ubuntu9.04 / mythtv?"
date: 2009-08-31
forum: Multimedia Software
---

### Post by marmiteOlz on 2009-08-31
hi all, need some advice
i installed mythtv today on my ubuntu9.04 drive as i want to get a tv tuner card for a pc (so i can slowly without the wife noticing any costs)
obviously i want it to be linux compatible and a good all rounder
i would prefer a card with a aerial connection ( cant see a connection on a usb version) as my area has a very weak signal ( have satelite tv) and my external aerial needs replacing.
it would have to be a good tuner for weak areas as i had to enable  the LNA on my tv dvt card to pick up any signal and using my aerial on 1-2 channels played without stuttering.
so  whats a decent model digital tv tuner and whats one to avoid.

thanks in advance..
btw im in the UK just in case it makes a difference

---

### Post by marmiteOlz on 2009-09-08
ok either 1 person went refresh mad and viewed the topic 55 times
or no one can recommend a tv tuner card

---

### Post by NinjaNumberNine on 2009-09-08
[URL="http://www.compuvest.com/Desc.jsp;jsessionid=aXlM_ouZfghb9gJCAo?iid=908301"]??
WinTV PVR-150MCE[/URL]
[Reviews (Notice the ones about linux users)]("http://www.amazon.com/Hauppauge-WinTV-PVR-150MCE-Non-FM-Remote-274/product-reviews/B000E65HOO/ref=dp_top_cm_cr_acr_txt?ie=UTF8&showViewpoints=1")
-and thats about the best deal you'll get for 30-40 dollars.

EDIT: Oh, sorry, didn't see that you wanted digital.

---

### Post by marmiteOlz on 2009-09-08
thanks anyway... guess ill have to keep my eyes open for reviews

---

### Post by NinjaNumberNine on 2009-09-08
Analogue is very good quality though, and NTSC tuner cards have better Linux support in general than do ATSC. I use the same cable for an ATSC and NTSC tuner; it seems they both get the same signal, digital is just way better quality. Hauppage cards are supposedly the best TV solution for linux for their decent price, semi-official linux support, (see here) and they do sport digital and analogue capture cards.Overall, I happen to prefer analogue, but every man to his own taste, here's another great deal on a** digital** dvb-s card: [http://www.vesalia.de/e_skystar2%5B3818%5D.htm?slc=us](http://www.vesalia.de/e_skystar2%5B3818%5D.htm?slc=us)
this is the mythtv summary: [URL="http://www.mythtv.org/wiki/Sky_Star_2_TV_PCI"]http://www.mythtv.org/wiki/Sky_Star_2_TV_PCI
[/URL]

---

### Post by chinoy on 2009-09-10
You didnt mention what you want to do with it. 
You didnt mention what connection your willing to live with i.e.
PCI or USB or PCMCIA or ExpressCard.

Spent 6 months researching this and the best was a 65$ Express Card LifeVIew M5 MST tuner card.
Reasons why I picked this.
a. It has two Tuners that can be configured as Analogue or Digital or a mixture of both.
b. It has very good Mpeg2 compression either its hardware based or the s/w is really good it would record TV and CPU utilisation was under 15% 

Too bad nobody can tell me how to get it to work in Ubuntu.

---

### Post by NinjaNumberNine on 2009-09-10
>  Spent 6 months researching this and the best was a 65$ Express Card LifeVIew M5 MST tuner card. I have tried and tried to get these working as well, but they use the saa700(I probably misspelled that) chipset and I could not get the drivers setup.> Too bad nobody can tell me how to get it to work in Ubuntu. 	 Well isn't that the point? ;-)

---

### Post by chinoy on 2009-09-10
WOW for the first time I run across somebody who knows what card Im talking about Im over the moon with joy.

Please share with me any and all info about this card.

BTW I was able to get the card to work.
Only problem is I dont remember how.
Many formats latter and many OS installs latter it has stoped working.

The first time I got it working was in Vista. Vista just detected it as a Philips SA1762 Tuner card and everything worked.

Then I went to XP and it worked there too.

Everything went for a Six when I tried to reconfigure it to allow me to hook up my handy cam thru composite in.

I got my card from an Auz company called GDB.
On their site they have vista certified drivers. And software.

I even found one guy who got it to work in Linux something about having to output a string thru GPIO.
My take is that Ive upset the firmware on the card and I need to know the right GPIO commands to get it to work or reset the firmware.
Or I need to flash it with fresh firmware. I was under the impression it was using the SAA1762 IC where did you get the info on the SA7000 ?

---

### Post by marmiteOlz on 2009-09-10
thanks for the card details.. but i would be after a linux compatible one...
but if i want to run it on windows ill give it a looking over

regards to use..
a dual tuner would be ideal.. and digital preferably as the signal will be digital only 2011/12 in my area 
and would prefer a pci/pci-e card as i have enough usb items to live with atm

---

### Post by steefjeqv on 2009-09-10
Hi,

This should work :

[http://www.hauppauge.co.uk/site/products/data_novat500.html]("http://www.hauppauge.co.uk/site/products/data_novat500.html")

Read this first though :

[http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI]("http://www.mythtv.org/wiki/Hauppauge_WinTV_Nova-T_500_PCI")

TV card producers tend to change a type's specifications while keeping the name. This sometimes leads to a non-recognized card in a linux system.

Greetings,
Steven

---

### Post by NinjaNumberNine on 2009-09-10
I think he wants dvb-s (satellite) though.

---

### Post by NinjaNumberNine on 2009-09-10
> I was under the impression it was using the SAA1762 IC where did you get the info on the SA7000 ?
                                             I was just spitting it out the back of my head and I couldn't remember the whole thing, just saa7##.

---

### Post by chinoy on 2009-09-11
90% of these guys use a generic Philips IC tuner which Philips has released BDA complaint drivers for.
I honestly couldn't care about the TV bit I just want to get my handy cam tapes over the past 20 years onto the PC because the tapes have fungus and may not last very long.
These are personal family tapes so I dont want to give them to a shop.
When I had it working. TV worked both Digital and Analogue. (We only have analogue in our country no plans for satellite.

I have taken this up as a personal challange to get it to work.
But the truth is no where on the net have I found a Singla Dell Laptop owner with my modell and a working Express Slot.
Dell Support sucks.

Ps: This is for a Dell XPS M1530 its a laptop so all those PCI cards wont work.

---

### Post by NinjaNumberNine on 2009-09-11
-Get an HP. They have perhaps the best support available. Me buy HP PC just for break it and get nice support lots of time. :D

---

### Post by chinoy on 2009-09-12
It took me 2  years to plan and buy this kit.
Its not like the west where you change laptops at the drop of a hat.
These are almost lifetime purchases.
Whish I was back at work. COuld ask my Dept / Boss for a new laptop and as I was normally responsible for all purchases Kick Dell out.

---

