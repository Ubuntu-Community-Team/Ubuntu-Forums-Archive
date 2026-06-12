---
title: "Wifi question"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by magical2hobo on 2011-04-03
I recently dual booted my Dell Studio 1458 with Ubuntu and everything works fine but the wireless seems to have some issues. When I run under Windows I have full signal strength but when I'm using Ubuntu the signal strength drops to about 50% and every now and then it will drop the wifi signal even tho I'm about 10 ft. from my wireless router. Is there anything I can do to fix this? Also I'm really new to Linux and I don't remember my computer's specs exactly. :confused:

---

### Post by walt.smith1960 on 2011-04-03
Do you have any indications that your network is having a problem besides the signal strength meter?  You said it "drops the wifi signal".  Do you get disconnects, "page not found" errors, paused downloads, that sort of thing, or is it just the signal strength meter saying the signal is weak?  The signal strength meter (Network manager) used to be not very reliable, it would indicate a weak fluctuating signal strength when in fact the signal was in fact fine.

---

### Post by magical2hobo on 2011-04-03
> **walt.smith1960 said:**
> Do you have any indications that your network is having a problem besides the signal strength meter?  You said it "drops the wifi signal".  Do you get disconnects, "page not found" errors, paused downloads, that sort of thing, or is it just the signal strength meter saying the signal is weak?  The signal strength meter (Network manager) used to be not very reliable, it would indicate a weak fluctuating signal strength when in fact the signal was in fact fine.

Not really that's just the only thing, and ya when it disconnects I lose internet and web pages won't load and downloads stop and everything. So could the problem be with how the software isn't interacting with my wireless card right or something?

---

### Post by walt.smith1960 on 2011-04-03
> **magical2hobo said:**
> Not really that's just the only thing, and ya when it disconnects I lose internet and web pages won't load and downloads stop and everything. So could the problem be with how the software isn't interacting with my wireless card right or something?

There are people here MUCH more knowledgeable than me when it comes to wireless problems. I assume the card is in the machine? If so, posting the output of the command "lspci" might be a start to find out what wireless chipset in in your Dell.

---

### Post by magical2hobo on 2011-04-03
> **walt.smith1960 said:**
> There are people here MUCH more knowledgeable than me when it comes to wireless problems. I assume the card is in the machine? If so, posting the output of the command "lspci" might be a start to find out what wireless chipset in in your Dell.

Ya its an internal chipset. I ran the command you said and rather than posting the whole thing I'm guessing this is the one that you were talking about? I'm not entirely sure tho, hope it helps.


06:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)

---

### Post by walt.smith1960 on 2011-04-04
> **magical2hobo said:**
> Ya its an internal chipset. I ran the command you said and rather than posting the whole thing I'm guessing this is the one that you were talking about? I'm not entirely sure tho, hope it helps.


06:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)

Yes, that's the correct line.  I'm guessing that's a really new chipset.   I'd enable wireless  backports in case there's an updated module or something out there. Install, update, reboot and see if it's any better.  This is what fixed a problem I had with an Asus Netbook a couple years ago. There have been cases of enabling backports causing problems so be aware of that possibility.  If you have anything on your system that you'd be royally screwed if you lost it, back it up! Of course that's excellent advice regardless.  Here might be something of interest as well:

[http://www.intel.com/support/wireless/sb/cs-006408.htm](http://www.intel.com/support/wireless/sb/cs-006408.htm)

As a last resort there's NDISwrapper.

---

