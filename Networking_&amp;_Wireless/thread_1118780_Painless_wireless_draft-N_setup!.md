---
title: "Painless wireless draft-N setup!"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by wkulecz on 2009-04-07
I got fed up trying to find the "right" wireless N card and drivers for 8.04 and came up with a solution that while costing a bit more, has so far more then paid for itself in time saved.

I got a Linksys WGA-600N "wireless gaming adapter".  But what it really is, is a self-contained wireless client with transparent pass through to 100BaseTX Ethernet.

I setup my security and passphrase using the built in web interface, set it for DHCP (on Windows, where you have full manufacture's support for getting it setup! But it was trivial -- I never bothered to RTFM beyond [http://192.168.1.250](http://192.168.1.250)).   Reboot the box and restart XP networking and presto wireless N access on my XP laptop.  

Big deal you say, but here is where it gets good. I shutdown XP and moved the WGA600N to the Ethernet port on my Ubuntu 8.04 system and enabled wired networking and presto! wireless N connection on Ubuntu with no muss, no fuss!

At ~$100 its not all that much more expensive than other wireless N options.  For wireless G, the Airlink AP431W which Fry's has had on sale for $20 recently should do the same thing, but I haven't personally verified it.

Have transferred multi-GB of data with it over the weekend with zero issues, even did a couple of unnecessary Ubuntu reboots to verify its robustness.

--wally.

---

### Post by wkulecz on 2009-04-10
Bump.

Looking at all the pleas for help and mostly lack of solutions for anyting other than wide open wireless networks, I think more people need to know about this alternative.

The marketing materials of the WGA makes it appear they are only for Playstation or Xbox, its only in the "fine print" that you find out its really a generic device -- I'm using them on  Ubuntu, and our Direct TV set top box to download "on demand" programming.

Most any wireless access point that supports "wirless bridge mode" should also work, unfortunately most have this function disabled in the firmware and require you buy a higer priced "Access Point" version for this feature.

Letting the WGA or AP Bridge handle the 802.11 connections and security settings enables you the get it set up using Windows with full support from the manufacturer and then just use Linux's wired networking which is very soild and mostly trouble free.

Only real downside is if you need to use a full mobility notebook running on battery poewer, but I've never found battery life to be long enough to be useful in this mode, especially when doing a lot of data transmission.

--wally.

PS the gigabit wired update rocks, I feel stupid for being so cheap and putting it off for so long!

---

### Post by wkulecz on 2009-04-17
Finally found a good link to this device specs:

[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175239647577&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4757724212B05](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175239647577&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4757724212B05)

As I said, most of its marketing materials suggest it is only for Xbox or Playstation.

I bought it at Fry's so I could return it if it didn't work as advertised, worked so well I bought another to add wireless internet connection to our DirecTV receiver.  I'll likely be getting a third for my XP notebook eventually as my Airlink101 AWLC-5025 Cardbus card's XP driver blue screens in the presence of a draft-N router :(  (Still works fine if only 802.11g is available) but 90% of the time I use my notebook either I don't need a network connection or I can use the wire.

--wally.

---

