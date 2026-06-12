---
title: "Micro Server and Low Profile Digital Tuner Card"
date: 2011-03-19
forum: Mythbuntu
---

### Post by Mad-Halfling on 2011-03-19
Hi folks, I'm finally getting around to setting up MythTV at long last, and I wondered if I could please pick your brains about a couple of things.

I'm wanting to set up a headless server then fire the content over the network to my laptop - I was looking at getting one of these servers as they're cheap with the cashback, this should run fine, correct?
[http://www.it247.com/product/1/COMSU...-warranty.html](http://www.it247.com/product/1/COMSU...-warranty.html)

I am in the UK and want to push the server in between my aerial wall socket and a "normal" digital TV box, so I figured on getting a digital input card with a coaxial input and output - would the output socket usually act like a straight-through socket so that I can just link that to my existing digital box and that can view whatever it wants, irrespective of what the MythTV box is doing, or would I need a splitter?

Also, can anyone recommend any low profile digital tuner cards, please? I want to get an OK one, but not break the bank too much (but I have a decent budget, if necessary).

Thanks for any help you can give me - I'm a techie person but I've been out of the loop on hardware for a while now.

MH

---

### Post by ian dobson on 2011-03-20
Hi,

Firstly your link doesn't work. The backend server doesn't really need much CPU, recording a digital stream is nothing more than copying the data from the tuner card to the harddisk.

Disk space is all that the server really needs, just make sur eyou have enough.

You don't say what signal your getting (DVB-c/t/s) so I can't say what tuner card to get. Have a look at [www.linuxtv.org](www.linuxtv.org) for a list of supported cards. For DVB-t/c you can use the pass through for the antenna or just use a T piece.

Also be careful if your signal is encoded/payTV you'll need to get a card to decode the signal.

Regards
Ian Dobson

---

### Post by Mad-Halfling on 2011-03-20
Sorry about that link, hopefully this one may work:-
[http://bit.ly/evEvDB](http://bit.ly/evEvDB)
As far as I'm aware that can only take up to 25W cards and it only has low-profile slots so I may be limited in what I can use (and may have to go USB)

Sorry to be such a noob, but this is the first time I've had to get into digital reception - I have no idea what signal type I would be receiving - I will be using an existing analog aerial (we don't have satellite tv, or anything like that) and just looking to receive the basic, free-to-air services available in the UK.  I am in south east Essex, in the UK - is there somewhere I can check which service I would be receiving (poking around, I suspect it would be DVB-T as that seems to be the European terrestrial service format)?

Thanks, and sorry for not being able to provide as much information as is needed, but as I said I've not looked into digital reception H/W so far and as I'm a bit out of the loop with my hardware knowledge as I've used laptops for the last 5 years and so haven't built a PC from scratch for ages =8)

Is there any other information I need to find out?

Cheers

MH

---

### Post by ian dobson on 2011-03-21
Hi,

That looks like a really odd ball system, I'm not sure if it even supports add in cards (PCI or PCI-e).

Maybe have a look for a different system, thats more PC conform. Also if you have DVB-t then you should be able to use one of the many USB tuners available. As I've already said have a look at [www.linuxtv.org](www.linuxtv.org).

Regards
Ian Dobson

---

### Post by vskatusa on 2011-03-21
Generally, we use any old pc as a server. That is what I am doing instead of spending on new hardware. Off course one can make an argument to use the latest cpu for power savings

---

### Post by Mad-Halfling on 2011-03-21
I got it primarily to be a network storage device, as it's cheap with the cash-back (£150), but then thought it might be useful as a mythTV server.  It's Linux compatible (RHEL is an OS option on it) and it does has slots (from the tech spec listing):-
1 x PCI Express 2.0 x16 - half-length, low-profile
1 x PCI Express 2.0 x1 - half-length, low-profile
1 x PCI Express x4

My problem with using an old PC is
a) I don't have one or, rather, all my old ones are rather ancient (at least 8 years old)
b) space near my aerial outlet is limited and any unit has to be pretty quiet so I don't have the room for a full tower (unfortunately, running new cables around isn't really an option, either)
so if I _could_ get that running as a server it would be ideal.  The guy who put me onto it has bought one and he says it's a nice little bit of kit, he's got another one coming that he's going to use as a media machine to stream content to his TV

---

### Post by Rhubarb on 2011-03-21
If you can receive DVB-t (which you most likely can, though I can't say for sure - go into your local TV shop and see if any have digital tuners in their tv sets), then you don't have to consider 1/2 length low profile cards.
Instead you can also look at usb dvb-t tuners.

I've got 2 Asus U3100 usb tuners in my little zotac box and they work fine.

For reference my little zotac box is the front and backend for mythtv (mythbuntu), and the specs are:
Dual-core 1.6GHz 64bit atom with hyper threading, NVIDIA ion video, 320GB laptop HDD, 2GB RAM.

It's plenty more than enough to watch a high-def tv show and record another high-def tv show at the same time.

Note that I've personally had troubles getting a mythtv combined front and back end working with another front end.  I didn't spend much time on trying though.

As a network storage device that little HP server would do quite well too :D

---

### Post by Mad-Halfling on 2011-03-21
> **Rhubarb said:**
> If you can receive DVB-t (which you most likely can, though I can't say for sure - go into your local TV shop and see if any have digital tuners in their tv sets), then you don't have to consider 1/2 length low profile cards.
Instead you can also look at usb dvb-t tuners.

I've got 2 Asus U3100 usb tuners in my little zotac box and they work fine.

For reference my little zotac box is the front and backend for mythtv (mythbuntu), and the specs are:
Dual-core 1.6GHz 64bit atom with hyper threading, NVIDIA ion video, 320GB laptop HDD, 2GB RAM.

It's plenty more than enough to watch a high-def tv show and record another high-def tv show at the same time.

Note that I've personally had troubles getting a mythtv combined front and back end working with another front end.  I didn't spend much time on trying though.

As a network storage device that little HP server would do quite well too :D

Ah, that's really interesting to know - I was primarily looking at an internal card as I figured it would perform a lot better than a USB device - I can't imagine I'd be doing much more than either watching a show or recording one if I wasn't around, so I wouldn't need too much poke to it - I take it you have 2 USB tuners so that you have the option to watch and records simultaneously?  Are those Asus tuners current models?

I was thinking of getting a lowish level GFX card to help with the program processing, something like this
[http://www.dabs.com/products/zotac-geforce-gt-210-512mb-pci-express-2-0-hdmi--synergy--6BGQ.html?utm_source=google&utm_medium=product+search](http://www.dabs.com/products/zotac-geforce-gt-210-512mb-pci-express-2-0-hdmi--synergy--6BGQ.html?utm_source=google&utm_medium=product+search)
would that be enough or would I need a beefier one?

Thanks for your help, it's much appreciated it.  The server arrived today and it seems a nice little bit of compact kit, will try to experiment with a load up tomorrow (I'll reload when I get the tuner hardware, additional disks and maybe more memory)

MH

---

### Post by Rhubarb on 2011-03-21
> **Mad-Halfling said:**
> ...I take it you have 2 USB tuners so that you have the option to watch and records simultaneously?  Are those Asus tuners current models?
Yes, I use the 2 tuners so I can watch one and record another channel simultaneously. (or record 2 channels, and watch nothing).
The Asus tuners probably wouldn't be current models - as I've seen them around for about 3 years.  Some shops I've noticed still have very low stock (atleast in my area anyway).
I'm pretty sure this is the model tuner I've got:
[http://www.asus.com/product.aspx?P_ID=NnLlh0UmHlvpDzhB&templete=2](http://www.asus.com/product.aspx?P_ID=NnLlh0UmHlvpDzhB&templete=2)
It's not the same colour, but it looks to be the same one.
> **Mad-Halfling said:**
> ...I was thinking of getting a lowish level GFX card to help with the program processing, something like this
[http://www.dabs.com/products/zotac-geforce-gt-210-512mb-pci-express-2-0-hdmi--synergy--6BGQ.html?utm_source=google&utm_medium=product+search](http://www.dabs.com/products/zotac-geforce-gt-210-512mb-pci-express-2-0-hdmi--synergy--6BGQ.html?utm_source=google&utm_medium=product+search)
would that be enough or would I need a beefier one?
That is plenty beefy enough!
With nvidia cards you can use vdpau to accelerate video playback.
I'd check to see if you can play any old mpeg2 / mpeg4 video on your little hp server's video out first - you may be pleasantly surprised.
- The website for you hp doesn't say what internal video it has, if it's horrible and doesn't play back videos well, consider getting that zotac video card.

As others have said here, playback / recording of DVB-t TV is really quite an easy thing for most computers.  The stream you get from the tuner is just Mpeg2 or Mpeg4.  MythTV just essentially dumps it to disk or plays it back.  MythTV can also re-encode videos and flag recorded TVs for commercials so you can easily skip past them.

Anyway, as a file server (and eventually anything else you can think of whacking on that little box) it's pretty cool!

---

### Post by Mad-Halfling on 2011-03-22
As I understand it, a GFX card in there can help with the processing, even if I'm just recording stuff on that box and not viewing it on there, correct?  I was going to use this as back-end server and access the content on there on my laptop and wouldn't (certainly, at the moment) have a monitor or TV hooked up to that box - am I correct in how I understand MythTV works, in this way?

Thanks for all your help folks, this has been the most helpful forum I've posted on.

Hopefully that little box should do me proud - esp as with the cashback it works out to the equivalent of 250 bucks, Australian, rather than the RRP equivalent of 400 =8)

---

### Post by ian dobson on 2011-03-22
> **Mad-Halfling said:**
> As I understand it, a GFX card in there can help with the processing, even if I'm just recording stuff on that box and not viewing it on there, correct?  I was going to use this as back-end server and access the content on there on my laptop and wouldn't (certainly, at the moment) have a monitor or TV hooked up to that box - am I correct in how I understand MythTV works, in this way?

Thanks for all your help folks, this has been the most helpful forum I've posted on.

Hopefully that little box should do me proud - esp as with the cashback it works out to the equivalent of 250 bucks, Australian, rather than the RRP equivalent of 400 =8)

Hi,

In theory a graphic card can be used for computational work (NVidia CUDA) but Linux/MythTV don't use it at the moment. 

In my backend I have the oldest cheapest Graphic card I could find (NVidia 7200), as the box doesn't even have a monitor I shouldn't even need that, but the BIOS is so screwed up that it doesn't boot if no graphic card is installed.

Regards
Ian Dobson

---

### Post by Mad-Halfling on 2011-03-22
Ah, that's interesting - I was under the impression that a GFX card could still be useful in a server, either for processing the incoming video/audio streams or for firing them out across the network (I wasn't sure if that was and/or), but is that *only* if you are directly outputting video to a monitor/TV then?

As a matter of interest, CUDA works fine on Linux - I was playing with it over Christmas with my brother, though if you try it currently (or, this was the case 3 months ago) IIRC the proprietary NVIDEA version seems to run better than the open source one.

---

### Post by ian dobson on 2011-03-22
Hi,

Maybe CUDA is supported under Linux but the API isn't that stable and there aren't any real programs that use it at the moment. MythTV only used VDPAU for hardware acceleration on the frontend, and the backend doesn't even need a graphical interface.

Linux isn't like windows, the server component for a graphical interface can run on one computer with the graphical application, and the actual graphical display runs on a different one. On windows most remote desktop programs "scrape" the graphical output from the program and transmit it over the network.

The proprietary NVIDIA driver is better at decoding/displaying video than the open source one, as NVidia haven't provided the required information to the community (If thats good/bad/evil is not something I want to get into).

Regards
Ian Dobson

---

### Post by Mad-Halfling on 2011-03-22
> **ian dobson said:**
> Hi,

Maybe CUDA is supported under Linux but the API isn't that stable and there aren't any real programs that use it at the moment. MythTV only used VDPAU for hardware acceleration on the frontend, and the backend doesn't even need a graphical interface.

Linux isn't like windows, the server component for a graphical interface can run on one computer with the graphical application, and the actual graphical display runs on a different one. On windows most remote desktop programs "scrape" the graphical output from the program and transmit it over the network.

The proprietary NVIDIA driver is better at decoding/displaying video than the open source one, as NVidia haven't provided the required information to the community (If thats good/bad/evil is not something I want to get into).

Regards
Ian Dobson

We were messing about with CUDA to try it out and do maths calculations, that's pretty much all it's being used for at the moment, as far as I know (and it's current raison d'etre).  Thanks for the outline - I'm well aware of the differences between windows and Linux (I was compiling LAMP servers from source 8 or 9 years ago, lol and was an HP-UX admin for a few years before that), but I could have sworn I read something somewhere about MythTV being clever and using GFX cards at the back end, too - but it turns out I was wrong.
Now I've just gotta ort myself out a tuner and I'm rolling.

Thanks for the help, folks, much appreciated

Oh, and if you're in the UK, those microservers look like nice bits of kit, with the £100 cashback, if you want a small server unit =8)

---

### Post by Rhubarb on 2011-03-22
> **Mad-Halfling said:**
> Oh, and if you're in the UK, those microservers look like nice bits of kit, with the £100 cashback, if you want a small server unit =8)
Thanks but no thanks, I already have a tiny server (separate to my zotac myth tv box), the fit-PC2i
[http://www.fit-pc.com/web/fit-pc2/fit-pc2i-specifications/](http://www.fit-pc.com/web/fit-pc2/fit-pc2i-specifications/)
I can recommend it as a headless server, but not as anything that needs a graphical display (unless for a terminal). - It uses the intel poulsbo chipset which is terrible for gfx use.

---

