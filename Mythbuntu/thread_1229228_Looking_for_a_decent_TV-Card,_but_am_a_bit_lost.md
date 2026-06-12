---
title: "Looking for a decent TV-Card, but am a bit lost"
date: 2009-08-01
forum: Mythbuntu
---

### Post by a3uge on 2009-08-01
Hey guys, I have a couple of questions from a confused dude, who's mind has been splitting looking at installation guides, product reviews, and tutorials. The problem is, I haven't bought anything yet and want to avoid problems in the installation. So I was hoping someone could help me out. Here's the situation:

[LIST]
[*]I live in the USA, I have cable TV, which is split about 15 times, going into different rooms in the house, and I'm about the 3rd main split before it gets to my room. Does this mean I need a ATSC?
[*]I have a home-theater projector, with HDTV capabilities, but want to use a VGA input from my computer. Either that or a component hook-up. The HD isn't too big of a concern, but would be nice.
[*]Also have a decent 5.1 surround sound system.
[*]Want this in my old computer I used freshman year. It's a small Shuttle XPC, it has a PCIe slot which I'm using for my video card (NVIDIA GeForce 6200TC) and an open PCI slot. So unless using cheap onboard video is reasonable, I would need a PCI card. Computer has 1GB RAM and AMD 64-bit Athlon 3200? CPU. 
[/LIST]

So here's what I'm looking for.
[LIST]
[*]A card will look good for every-day TV use on the projector
[*]Record shows, or two shows at once if one card can do that?
[*]Is under $250, and is sold at a reasonable online store
[*]Has a reasonable set-up, with support I can find in case someone had the same issue.
[/LIST]

From what I hear, the Hauppanauge PVR-150 is the most supported and easy to set up card, but I have concerns with the quality, especially on a large screen. Are the Hauppanauge PVR-1000+ models much harder to set up? If I get a card listed in here: [http://www.linuxtv.org/wiki/index.php/ATSC_PCI_Cards](http://www.linuxtv.org/wiki/index.php/ATSC_PCI_Cards) should I be golden? How much of a guru do I have to be to set one of these things up? I've been using Ubuntu for three years now, and am aware of how things can magically screw up when tinkering.

Thanks for any help, direction, or guidance.

---

### Post by klc5555 on 2009-08-02
> **a3uge said:**
> Hey guys, I have a couple of questions from a confused dude, who's mind has been splitting looking at installation guides, product reviews, and tutorials. The problem is, I haven't bought anything yet and want to avoid problems in the installation. So I was hoping someone could help me out. Here's the situation:

[LIST]
[*]I live in the USA, I have cable TV, which is split about 15 times, going into different rooms in the house, and I'm about the 3rd main split before it gets to my room. Does this mean I need a ATSC?
[*]I have a home-theater projector, with HDTV capabilities, but want to use a VGA input from my computer. Either that or a component hook-up. The HD isn't too big of a concern, but would be nice.
[*]Also have a decent 5.1 surround sound system.
[*]Want this in my old computer I used freshman year. It's a small Shuttle XPC, it has a PCIe slot which I'm using for my video card (NVIDIA GeForce 6200TC) and an open PCI slot. So unless using cheap onboard video is reasonable, I would need a PCI card. Computer has 1GB RAM and AMD 64-bit Athlon 3200? CPU. 
[/LIST]

So here's what I'm looking for.
[LIST]
[*]A card will look good for every-day TV use on the projector
[*]Record shows, or two shows at once if one card can do that?
[*]Is under $250, and is sold at a reasonable online store
[*]Has a reasonable set-up, with support I can find in case someone had the same issue.
[/LIST]

From what I hear, the Hauppanauge PVR-150 is the most supported and easy to set up card, but I have concerns with the quality, especially on a large screen. Are the Hauppanauge PVR-1000+ models much harder to set up? If I get a card listed in here: [http://www.linuxtv.org/wiki/index.php/ATSC_PCI_Cards](http://www.linuxtv.org/wiki/index.php/ATSC_PCI_Cards) should I be golden? How much of a guru do I have to be to set one of these things up? I've been using Ubuntu for three years now, and am aware of how things can magically screw up when tinkering.

Thanks for any help, direction, or guidance.

Basically each thing watched/recorded simultaneously requires its own tuner.

1) PVR 150 is analog only --not ATSC. No digital input, no HD input. There are skazillions of them still out there, but they aren't sold new any longer in the states because they're analog-only.

2) The usual Haupauges like the 1600 and the dual-tuner (PCI-e) 2250 are reasonably easy to set up, but seem to suffer from significant signal-strength issues --may not be the best choices for cable input split 4-to-8 ways.

3)The PCHDTV-5500 is the closest thing to out-of-the box digital you're going to find with Linux, but is a tad pricey (at $114) and is a single tuner. Cheap Phillips-tuner-based cards like the the AverMedia 180 or similar will give you the same service for about $40-$80, but are often a bit tricky to set up. 

4)A network tuner like the Silicon Dust HD Homerun may well be thw gold standard for all the Mythtv tuner devices out there.

For Mythtv use, particularly if you hope to do HD, NVidia GeForce (6xxx and above) cards are almost always your best choice. Another half-gig or so of RAM would also be a good choice. Your processor may prove to be a bottleneck for HD (depending on other factors), but will work fine for standard digital. And analog, if this is a concern.

Digital consumes 1 Gig of hard disk storage per hour; analog 2.2; HD about 6.6 In addition to whatever disk you start off with the operating system and Mythtv on, if you plan to record much of anaything you're going to soon want to add a big, fast storage drive (or several) for recordings. Should be SATA (for speed), as big as you can afford (1 T drives are currently the price point at $90, and seem to be quite reliable) 

Cheers! :)

---

### Post by a3uge on 2009-08-02
Thanks for the detailed response. I have a couple of follow-up questions. I was looking at the AverTV a180 page [http://www.mythtv.org/wiki/AVerTV_HD_A180](http://www.mythtv.org/wiki/AVerTV_HD_A180) and it says "Therefore, it is highly discouraged for analog use" but I would be using digital anyways if I'm receiving a ATSC signal right? I like the pcHDTV HD card, it seems fairly idiot-proof, but I'm afraid of spending $115 on a non-name brand product that gets the same result as something cheaper. And I always have the fallback of a different PVR option with other supported cards.

What about the pcHDTV HD-3000? Is that a reasonable card, I see one on Ebay for $50.

I'm also drawn to the ATI HDTV Wonder, but the [http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_115](http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_115) KWorld ATSC seems fairly nice and supported.

Edit: I just bid on a KWorld ATSC-110, it's only $26, but with a day left I doubt my bid will last. Would this be a bad purchase?

Thanks for all the help!

---

### Post by klc5555 on 2009-08-03
> **a3uge said:**
> Thanks for the detailed response. I have a couple of follow-up questions. I was looking at the AverTV a180 page [http://www.mythtv.org/wiki/AVerTV_HD_A180](http://www.mythtv.org/wiki/AVerTV_HD_A180) and it says "Therefore, it is highly discouraged for analog use" but I would be using digital anyways if I'm receiving a ATSC signal right? I like the pcHDTV HD card, it seems fairly idiot-proof, but I'm afraid of spending $115 on a non-name brand product that gets the same result as something cheaper. And I always have the fallback of a different PVR option with other supported cards.

What about the pcHDTV HD-3000? Is that a reasonable card, I see one on Ebay for $50.

I'm also drawn to the ATI HDTV Wonder, but the [http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_115](http://www.linuxtv.org/wiki/index.php/KWorld_ATSC_115) KWorld ATSC seems fairly nice and supported.

Edit: I just bid on a KWorld ATSC-110, it's only $26, but with a day left I doubt my bid will last. Would this be a bad purchase?

Thanks for all the help!

The two KWorld varieties have the cheap Phillips tuner the same as the Avermedia 180, and should work basically the same.

It's a "cheap" Phillips tuner, because, while there are many related flavors of it, it doesn't include the hardware to identify itself properly to the driver module at startup. So odds are, when you have installed the card and do a plain-vanilla system startup, the card _may_ not work at first. However, once you have correctly identified the precise flavor of the card and tuner to modprobe, made sure the firmware file is loading, and have shut down and restarted the machine, the card works fine thereafter. As the page for the 110 indicates:

[http://www.mythtv.org/wiki/Kworld_ATSC_110](http://www.mythtv.org/wiki/Kworld_ATSC_110)

Occasionally, it takes a bit of research on the saa7134 driver on (of all things) the Gentoo linux wiki, or among the v4l online docs to find the precise modprobe parameters for particular Phillips tuners.

The Avermedia180 comes in two flavors nowadays. The old style card, where the use of analog is discouraged, and the new style card, where it doesn't have to be discouraged because all the analog circuitry and connections have been left off the card. Resellers don't often distinguish the two in their ads. They both work fine. 

The PCHDTV 3000 is the ancestor of the 5500, and was discontinued in about 2006. But it is still supposed to be supported, and ought to work fine "out-of-the-box" (both digital and slightly flakey analog) on current Linux kernels (as found in Mythbuntu 8.10 and 9.04), if you happen to latch onto one for cheap.

---

### Post by a3uge on 2009-08-03
Well I ended up winning the Kworld ATSC 110 on ebay. Kind of an accident, didn't think it'd go for that cheap, considering the remote alone was worth more than what I got the card and the firefly remote for.

Thanks for the help, if I can't install I'll probably be making a new thread after I desperately google for the answer.

Someone can close up this thread then.

---

