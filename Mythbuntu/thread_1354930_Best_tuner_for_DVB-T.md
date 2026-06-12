---
title: "Best tuner for DVB-T"
date: 2009-12-14
forum: Mythbuntu
---

### Post by timswait on 2009-12-14
After failing to get my Hauppauge HVR-1300 working under 9.10 (see this thread [http://ubuntuforums.org/showthread.php?t=1327514]("http://ubuntuforums.org/showthread.php?t=1327514")), I ended up having to go back to 9.04. However, now I'm looking to replace the HVR-1300 with something that's HD, and I'd like two tuners. I have looked through the hardware pages on linuxtv.org and Mythtv.org and past threads here, but everything seems to have some sort of issue, or else I can't find anywhere to buy it! So are there any cards that people have got completely working under 9.10 that they can fully recommend? My basic requirements are:
-Must be DVB-T
-PCI
-Must work with Mythbuntu 9.10
-Dual tuner preferable, but I may get two separate cards
-Must be HD ready.
Are there any that fit this? I've found this one for sale:
[http://www.pctvsystems.com/Products/ProductsEuropeAsia/Digitalproducts/PCTVDualDVBTPCI/tabid/180/language/en-GB/Default.aspx]("http://www.pctvsystems.com/Products/ProductsEuropeAsia/Digitalproducts/PCTVDualDVBTPCI/tabid/180/language/en-GB/Default.aspx"), but I can't find any reference to this card on linuxtv, so does anyone know if it'll work?
Cheers

---

### Post by Neon Dusk on 2009-12-14
From you location it looks like you're in the UK. 

At the moment they are no Freeview HD ready DVB cards. Freeview HD will need a DVB-T2 card

---

### Post by nickrout on 2009-12-14
HD can certainly be broadcast on DVB-T, but if your local provider has chosen to use DVB-T2 you are SOL right now!

---

### Post by timswait on 2009-12-15
Yes, am in the UK, that's annoying, no HD yet then. I'm still thinking I want to change to a dual tuner card though, has anyone any experiences of the PCTV Dual DVB-T PCI? Or what about the Hauppauge Nova T-500? There seem to be quite a few people having problems with it, but are these working in the latest Mythbuntu version now? (I'm using the 64 bit version).
Any other suggestions for cards that just work without problems in 9.10?
Is there such a thing as a TV tuner card that works properly without problems?!;)

---

### Post by SiHa on 2009-12-15
I've got a Nova-T 500, and while you do need to fiddle a (very) little bit to get it stable in 9.10(32 bit), it's really very simple.
I use a homebrew IR Receiver, so I can't speak for the remote functionality in 9.10.

---

### Post by byronmyth on 2009-12-15
I can vouch for the NOVA-T 500 too, a little config to get it to work with other cards in the system and for me at least it has been flawless.

---

### Post by byronmyth on 2009-12-15
Oh, and don't hold your breath waiting for a DVB-T2 card, I can see that being a long time coming, the UK (to my knowledge) is the only place playing DVB-T2 so no urge for making the chipsets to support it.
 
If you want to play HD get yourself a NOVA-HD-S2 card, sat dish aimed at Astra 2 (28.2E) and then bathe in the glorious wonder that is BBC HD, oh, and and the odd titbit on ITV-HD. You will be ready for the world cup then too :)

---

### Post by SiHa on 2009-12-15
...or be a cheapskate and get an old Nova-S off [[COLOR="Blue"]_eBay_[/COLOR]](http://cgi.ebay.co.uk/Hauppauge-WinTV-NOVA-S-Digital-Satellite-TV-Card_W0QQitemZ260523710268QQcmdZViewItemQQptZUK_Computing_Computer_Components_Graphics_Video_TV_Cards_TW?hash=item3ca86c573c). I got one from the same seller a few months back, and BBC-HD does look nice on it.

---

### Post by sneakerfreak on 2009-12-15
I've got the Nova T-500 as well and I didn't break any sweat making it work. I had some issues scanning for channels but apart from that I am really satisfied. The remote works perfectly as well though it didn't work out of the box. It is not hard to get to work though (lots of instructions on the net).

I would buy this card again if I had to replace it.

---

### Post by timswait on 2009-12-16
Thanks for all the info, it's great.
On the subject of satellite (am considering it), does it work like DVB-T where you can record multiple channels with a single tuner (as long as they're compatible with each other), or do you need multiple cards to do that?

---

### Post by nickrout on 2009-12-16
> **timswait said:**
> Thanks for all the info, it's great.
On the subject of satellite (am considering it), does it work like DVB-T where you can record multiple channels with a single tuner (as long as they're compatible with each other), or do you need multiple cards to do that?

yes dvb-s does multirec

---

### Post by timswait on 2009-12-25
How many freesat channels are compatible with each other? Is it like DVB-T where you can only multirecord (for example) BBC channels together, or can you record any combination of channels?

---

### Post by nickrout on 2009-12-25
> **timswait said:**
> How many freesat channels are compatible with each other? Is it like DVB-T where you can only multirecord (for example) BBC channels together, or can you record any combination of channels?

On one real tuner you can record anything on the same multiplex, ie on the same frequency. I believe this is a chart of the freesat channels:

[http://www.lyngsat.com/astra2d.html](http://www.lyngsat.com/astra2d.html)

---

### Post by pootle1 on 2009-12-26
The Nova S card has only 1 tuner, and at the  moment the muxes tend to be things like all the regional variants on the same mux, so you won't often find you can usefully get 2 things at once.  This is daft also because if they ever start using statistical muxing (to dynamically allocate bandwidth amongst the stations on a single mux), it won't do much good.  

At the moment even the best channels suffer regularly from compression artifacts even on static scenes due to lack of bandwidth *sigh*

Seems typical that today on satellite they still use S1 for HD even though we have S2 cards available, while on terrestrial HD, they use T2, and there are no T2 cards available.

btw, there is no certainty that when satellite moves to S2 for HD, that it will be accessible using open source / standards.

---

### Post by timswait on 2009-12-27
Thanks for your replies, helpful advice as always. I've splashed out and bought a Nova DVB-S2 HD card, a dish, and have done a fresh install of Mythbuntu 9.10. Now I'm trying to get the dish aligned correctly. I've read [this guide,]("http://www.xtendedplay.co.uk/howto-installing-freesat.html") and am trying to follow it. I have the dish bolted up and connected to the back of the computer. I've pointed it roughly 28 degrees East of South, and have a audible signal meter (whistle gets higher pitched as signal gets stronger) in line. When I try and tune in with the scan for channels (I followed [this thread]("http://ubuntuforums.org/showthread.php?t=914766&highlight=astra+frequency"), and used the tuning parameters given by Pootle1 for Channel 4) I get a whistle from the signal meter and I can adjust the dish to get the highest pitch. So I know I'm pointing at a satellite, but I don't know if I've got the right one. It fails to find any channels and has a Signal strength of 0% and Signal to noise of 100%. On the guide in the above link it says that if you've got a set top box you can look up Network ID and Transport stream numbers to find out which satellite you're pointing at. Is there any way to do this in Myth, or any other way of knowing which satellite it's pointing at?

---

### Post by nickrout on 2009-12-27
> **timswait said:**
> Thanks for your replies, helpful advice as always. I've splashed out and bought a Nova DVB-S2 HD card, a dish, and have done a fresh install of Mythbuntu 9.10. Now I'm trying to get the dish aligned correctly. I've read [this guide,]("http://www.xtendedplay.co.uk/howto-installing-freesat.html") and am trying to follow it. I have the dish bolted up and connected to the back of the computer. I've pointed it roughly 28 degrees East of South, and have a audible signal meter (whistle gets higher pitched as signal gets stronger) in line. When I try and tune in with the scan for channels (I followed [this thread]("http://ubuntuforums.org/showthread.php?t=914766&highlight=astra+frequency"), and used the tuning parameters given by Pootle1 for Channel 4) I get a whistle from the signal meter and I can adjust the dish to get the highest pitch. So I know I'm pointing at a satellite, but I don't know if I've got the right one. It fails to find any channels and has a Signal strength of 0% and Signal to noise of 100%. On the guide in the above link it says that if you've got a set top box you can look up Network ID and Transport stream numbers to find out which satellite you're pointing at. Is there any way to do this in Myth, or any other way of knowing which satellite it's pointing at?

do u have your lnb set up properly in mythtv?

---

### Post by timswait on 2009-12-27
Yes, I do have the LNB set up.
I've just updated the firmware for the card following the instructions on the wiki for the HVR-4000. This has solved one problem, now I get sig  strength 84 %, Sig/noise 13 %, which sounds better and I get loads of channels :) The problem is that they're all encrypted :( So I've probably got the wrong sat. So is there any way to check the Network ID and transport stream numbers in myth?

---

### Post by nickrout on 2009-12-27
> **timswait said:**
> Yes, I do have the LNB set up.
I've just updated the firmware for the card following the instructions on the wiki for the HVR-4000. This has solved one problem, now I get sig  strength 84 %, Sig/noise 13 %, which sounds better and I get loads of channels :) The problem is that they're all encrypted :( So I've probably got the wrong sat. So is there any way to check the Network ID and transport stream numbers in myth?

I'm not sure, but the usual dvb-tools like dvbtune and scan should help.

---

