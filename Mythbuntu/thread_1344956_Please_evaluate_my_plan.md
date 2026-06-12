---
title: "Please evaluate my plan"
date: 2009-12-03
forum: Mythbuntu
---

### Post by eriktheblu on 2009-12-03
Main query: what tuner should I get?

Details:

I'm thinking about setting up an older computer I have as a MythTV DVR.

The box is an HP Pavillion 1130n:
2.2GHz processor
3 GB memory 
Decent Nvidia graphics card (the specific model escapes me, but works fine with Hardy and Karmic)
250GB HDD (I doubt I'll need it all; I might throw on some games for good measure)

Based on the Mythbuntu system requirements page, it should work fine (not really interested in HD)

I plan to use this as both back end and front end in my living room, and possibly broadcast to my primary machine (running Karmic) over the home network. 

One concern I have is the network. Back end machine would be networked wirelessly (G I believe). Would this be fast enough for remote viewing? I'm not needing spectacular quality; I just want to watch a news broadcast that I miss while at work.

The TV tuner has not yet been selected. I have an open PCI slot; the PCI express is occupied by the Nvidia card. I'd be willing to use a USB device, but would prefer PCI. 

Looking at the MythTV wiki and LinuxTV site has left me a bit confused. Many of the cards mention do not seem readily available. I'm currently looking at Hauppauge as a forerunner. I would appreciate any recommendations.

I currently get my TV through digital cable service (Charter is the company if it makes any difference; I'm in the United States which I believe does). I'd prefer not to be tied to the digital service since I may relocate to an area without.

If 3GB of memory is overkill for this project, I can easily find better use for it.

Apologies for the long post.

---

### Post by Chris Musampa on 2009-12-03
I can't help you with a tuner choice as I'm in the UK.  

My combined back/frontend machine is an athlon xp 2GHz (ancient single core) with 1GB ram and an old nvidia (gforce something or other) using the open source driver.  Since installing Karmic last weekend cpu rarely gets over 40% (htop) while viewing standard def TV (was around 50 - 70% with jaunty).

As for network, my backend is wired but I regularly use this old laptop as a front end, it has never once had bandwidth issues viewing sd over wireless G.

---

### Post by blackoper on 2009-12-03
1GB of memory is plenty

For a pci capture card, you can't go wrong with the pvr-150 from hauppauge. Just get a used one cheaply and call it a day. Don't get the pvr-500 (dual tuner) as they do not have good picture quality.

There have been a lot of problems with wireless networking and myth in the past. How well the wireless and myth will work depends entirely on how your home propogates wireless signals. It may work, it may not. Usually it's easier to just use a wired connection. A lot of the people that were using wireless in the past have switched to the powerline ethernet option so they can use their electrical outlets/wiring. It's not as fast as ethernet, but it's plenty fast for myth and none of the wireless issues.

---

### Post by eriktheblu on 2009-12-04
Thanks for the recommendations and reassurance.

As appealing as the PVR-150 is, finding one from a trustworthy source is proving a problem (I don't care how good someone's ebay rating is; buying used computer components from strangers is not my favorite kind of investment).

---

