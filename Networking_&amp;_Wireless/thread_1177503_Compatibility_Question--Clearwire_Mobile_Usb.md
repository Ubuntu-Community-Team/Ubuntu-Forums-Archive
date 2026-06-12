---
title: "Compatibility Question--Clearwire Mobile Usb"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by paulderol on 2009-06-03
Ahoy All.

Clearwire has recently rolled out their services to the Metro Atlanta area and i am considering purchasing both a home and mobile bundled plan, but i can't seem to find much out about their usb modem/dongle dealie. Their website claims Windoze and upcoming OSX compatibility, and tech support SAYS that i could be able to do it, based on the network and the device, but i was hoping someone from one of the older Clearwire markets [portland, baltimore] could shed some light on the ability of the wimax dongle to communicate easily and simply with NM. 

i THINK the device is

Expedience Broadband Express Card
Model: PCEx25100

BUT i don't know for certain. The offering is not pcie, but further questions abound about those too....mostly just hunting confirmation that the usb mobile modem works under ubuntu. This is all for an Eee Pc running Eeebuntu, if that makes any difference.

Thanks Gang....

---

### Post by Mr_Mischif on 2009-06-25
Hey,

I'm in the same boat as you, I want to get clear too but I didn't know if the USB modem would work. I talked to whatever the title is of someone who chats with people and they said that the dongle won't work with Linux; if you want Clear you have to either go back to Windows or buy the Clear spot, which is another $140. They say they're working on some OSX drivers, so hopefully when those come out someone will adapt them for Linux.

PS where do you live in Atlanta? Like 10th street and up?

---

### Post by paulderol on 2009-06-27
i'm about to slide my way over into inman park by what amounts to sheer fantastic luck, and was probably going to go with the home plan anyway just because i'd prefer to encourage the new, and i don't have to have a phone line or cable, neither of which i use. The USB dongle dealie is Motorola, for the record, and no, it is not compatible, but not much work has been done on the wimax stack, so i don't think that any wimax modem will work with linux yet, but once any single one does, it'll be possible to connect to them, for now, the home modem is a standard network cable-accepting, stadnalone device that may be crippled. 

didn't see anything about the clear spot, but i'm not stepping up to the business plan plate.

glad someone noticed this post, i was getting lonely.....

---

### Post by paulderol on 2009-07-16
update for those who would wonder. 

Clear cannot deliver its promised speeds or reliability to my domicile. i live in a big concrete and steel cage. this is probably why. the usb dongle is not supported by the linux wimax stack *yet* and the clearspot wireless router [which enables cross-platform use of the mobile service], costing 120USD did not seem to be worth it as downtown is soaked in wifi that i can use, and there is little other need. switched to crumcost due to speed and general reliabitily, due to simply needing it now. i know, lack of net neutrality and all, but meh. there are no choices to evade either phone monopoly's wiretapper room or crumcosts poor policy choices. 

current status--displeased with providers generally, as is the trend these days.

---

### Post by cjeness on 2009-07-17
I live in Atlanta close to Peachtree and 19th Street.   Our Clear home and mobile modems just arrived.   We are looking for an alternative to BellSouth DSL.  The home modem was easy to install and, of course, our Ubuntu computers have no problem with this solution.   Unfortunately, the speed is about comparable to BellSouth.   We picked the package which was supposed to provide 6 mb download and .5 Mb upload.  We actually get about 3 and .35.  

The Motorola USB modem was somewhat slower.   It worked without an issue on Windows XP.  I did not expect to find a Linux solution yet, but hope springs eternal.

I am also generally unsatisfied with the performance of Internet providers.

Has anyone done anything with Clear Wimax on Ubuntu?

Cindy Jeness

---

### Post by Uolirod on 2009-07-19
Nothing new to add, just my interest in a solution to the Clearwire/XOHM wimax situation. My usb dongle is a ZTE TU25 which doesn't have any linux support either.

---

### Post by opm8 on 2009-08-26
I just signed up for Comcast "HighSpeed2go" 4g service (apparently it's re-branded Clear wimax service) here in Portland, OR and will be testing out the ZTE Tu25 (with expected results).  I did however, find a solution for using this USB device in a 3g/4g router.  Specifically the Cradlepoint CTR500.  Cheapest I could find was about $160 including shipping.  It works like a regular router but you plug in the USB device as the WAN input and it provides a wifi signal or ethernet jack to connect to.  There's also a CBA250 with no wifi for about $20 cheaper.

Pricey but at least it will work.  I'll end up buying one of these if the Comcast speed is worth it, otherwise will cancel the service.  Currently for my laptop I use the Cricket UTStarcom UM100C USB device without any issues whatsoever (albeit it's not as fast as I'd like).

I'll post my findings in a couple days.

opm8

---

### Post by ewendkos on 2009-09-30
I want to join this bandwagon as well.

I recently purchased an MSI Wind U100 with the purpose of multi-booting and having that on a UMPC.  It shipped with Windows XP, but I loaded the Ubuntu Netbook Remix last night and am VERY impressed.

I have Clear WiMax and at home using my Linksys I have zero issues accessing the internet.  When I'm about town, I'd like to be able to use the Clear WiMax dongle that I paid for but I have yet to find Linux drivers for it.

If someone could either help me find some, or I've heard the community could develop this that would be awesome.

Otherwise, is anyone aware of other WiMax on board modems that might work in Linux for the MSI Wind?

Thanks all!

---

### Post by opm8 on 2009-09-30
> **opm8 said:**
> I just signed up for Comcast "HighSpeed2go" 4g service (apparently it's re-branded Clear wimax service) here in Portland, OR and will be testing out the ZTE Tu25 (with expected results).  I did however, find a solution for using this USB device in a 3g/4g router.  Specifically the Cradlepoint CTR500.  Cheapest I could find was about $160 including shipping.  It works like a regular router but you plug in the USB device as the WAN input and it provides a wifi signal or ethernet jack to connect to.  There's also a CBA250 with no wifi for about $20 cheaper.

Pricey but at least it will work.  I'll end up buying one of these if the Comcast speed is worth it, otherwise will cancel the service.  Currently for my laptop I use the Cricket UTStarcom UM100C USB device without any issues whatsoever (albeit it's not as fast as I'd like).

I'll post my findings in a couple days.

opm8

Sorry for the late update.  Having been unable to find drivers for the ZTE Tu25 I canceled the service with Comcast.  Also when I had it running from a Windows pc the wireless speed was ABYSMALLY SLOW.  I had one bar of signal strength at home and zero at work, which is only two blocks away from Clear's kiosk at the mall where they get great speeds.  Clear seems like all hype and no substance to me.

---

### Post by Xanderfoxx on 2010-01-18
Although i know that salesmen may say what they need to to get me to sign up, this is disappointing. :(

I was excited about seeing wimax rolled out so soon, thinking wimax would take a few years longer to roll out.

so, the dongle requires software stack support? that's strange, so it's not like ev-do where a simple ppp connection would suffice? there is a wimax tower directly across the street from me, with a massive antenna pointed right at my apartment complex, so the second it works with linux, i'm going to attempt to multi-home two using a linux router, as at&t caps bittorrent at 680 kb/s using u-verse, when my max speed is around 6 mb/s and i'm using private trackers with a good seed ratio, so no reason to go so slowly other than bittorrent cap. thank you so much for helping me and the others, guys! rawr, ubuntu! <3

:guitar: Ubuntu rocks! If clear's wimax network is as cool as i think it will be, then it wont be long till ubuntu supports the dongle out of the box. ubuntu can only get better :3

---

### Post by NIT006.5 on 2010-07-26
Hi all,

Don't suppose there have been any breakthroughs here in the last few months? I'm also on ZTE TU25 and desperate for a solution.

---

