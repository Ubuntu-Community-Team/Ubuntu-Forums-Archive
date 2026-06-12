---
title: "Will this work - Convert HD to non HD for low end?"
date: 2010-01-23
forum: Mythbuntu
---

### Post by colin-nz on 2010-01-23
Hi,

I have searched and found that my frontend (an HP T5720 with an Nvidia 6200) is not really going to cut it as a HD front end... which is fine as I planned to use it on a non HD TV anyway.

My backend is capable of recording and watching HD (a HD Homerun tuner and a Phenom ll X2 550 with a Nvidia GTS 250).

I have recordings and live TV (from the HD Homerun) in HD, that I plan to send to a HD front end in the future... but, I also want to watch live TV (from the HD Homerun) and any recordings on the low end front end (which can't handle the HD)...

So I guess what I am asking is can the back end convert my HD content on the fly for my low end front end to consume? If so, how do I set it up (I have not had much success so far :-( )

Thanks for any help.
Regards
Colin

---

### Post by nickrout on 2010-01-23
No, not on the fly. You can do a one time transcode but then they will be SD on all frontends.

There are transcode on the fly uPnP server programs available that may do what you want.

---

### Post by colin-nz on 2010-01-25
Ok, thanks for that (a bit of a bummer, but never mind).

Does anyone know if it is possible to get the HD Homerun to output in lower resolution?

Ideally I would have one tuner in HD and one non HD so at least my HP T5720 can watch live TV.

On a similar note, has anyone had any luck with a T5720 in HD?

Regards
Colin

---

### Post by nickrout on 2010-01-25
Can you put a vdpau capable video card in it? You'll need a pci-e slot.

---

### Post by colin-nz on 2010-01-26
Unfortunately it only has PCI...

I have my eyes on an Albatron 8400GS which is supposed to be PCI and VDPAU capable, but I think this card is full length, and the HP T5720 can only take half length cards (I believe)... the 6200  card I have fits fine though... it might almost be worth it just to try and see if I can 'make it fit'.

So it generally sounds like I need to go down the route of making a HD capable front end to watch live TV out of the HD Homerun... not sure I can make one as cheap as something like the Sage 'Front end' however... more investigation needed.

---

### Post by LowSky on 2010-01-26
Have you even tried to watch HD on the Frontend?

Because according to the link at the bottom the card can display DVD and HDTV-ready MPEG-2 decoding up to 1920x1080i resolutions, and TV is only 720p or 1080i, FYI no one broadcasts in 1080p

[http://www.nvidia.com/object/geforce6_techspecs.html](http://www.nvidia.com/object/geforce6_techspecs.html)

---

### Post by nickrout on 2010-01-26
> **LowSky said:**
> Have you even tried to watch HD on the Frontend?

Because according to the link at the bottom the card can display DVD and HDTV-ready MPEG-2 decoding up to 1920x1080i resolutions, and TV is only 720p or 1080i, FYI no one broadcasts in 1080p

[http://www.nvidia.com/object/geforce6_techspecs.html](http://www.nvidia.com/object/geforce6_techspecs.html)

Those specs MAY be referring to windows capabilities. 

Still, as you say, worth trying before investing in a new card.

There are reports of pci 8400gs cards working well with vdpau. Don't forget though that you can have an acer revo full HD front end for $199 in the US.

---

### Post by nickrout on 2010-01-26
Hold on, looking at Colin-nz's name, I assume he is in New Zealand and therefore his HD is h.264. That machine will never play h.264 HD without vdpau assistance.

---

### Post by colin-nz on 2010-01-27
Hi,

Yes, I am indeed in New Zealand... I have had a quick search and the only acer revos I can find here are way more (like more than double) the $200US mark...

So, unless I think about importing, looks like I may investigate the pci 8400gs with vdpau and hope it will work in the HP T5720 thin client, and hope it will work with our HD content here which sounds like it is H.264

Regards
Colin

---

