---
title: "Cisco WUSB600N rev 1"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by amiliv on 2010-09-17
There was quite a bit of threads about this card, and getting it to work mostly boils down to downloading Ralink's propitiatory driver.  The card uses RT2870 chipset, and Ubuntu comes with two drivers that are supposed to support it, neither of which seems to work with WUSB600N.  One of the drivers included with Ubuntu detects networks operating on 2.4GHz but fails to connect to them, but does not detect 5GHz networks at all.

I was wondering if anybody knows what is so special with this card that it doesn't work with drivers that are shipped with Ubuntu?  The card works nicely with Ralink's driver, but it's a bit annoying to have to recompile it on every kernel update (would be much nicer if it worked with stock drivers).

---

### Post by mick d on 2010-09-22
**I recently had a virus infect windows on my computer and decided to give ubuntu a try because I didn't want to feed the microsoft monster anymore. Looks very promising but I have read several threads on getting the linksys 600n working and it's overwhelming. I don't have a degree in computer programming and it appears you need one to do anything with ubuntu. I am trying to learn but am leaning to going back to windows as much as I hate it. **

---

### Post by amiliv on 2010-09-22
Well, no need to go back to Windows just because of this particular troublesome wireless card ;-)

Getting an unsupported piece of hardware to work on Windows is much worse nightmare (been there, done that).  Remember that Cisco's WUSB600N is not on the Ubuntu's list of supported hardware, and getting anything unsupported to work with any OS is always pain in the ***.  And I do sysadmin stuff for living.

I usually make sure that hardware I buy is fully supported in mainstream Linux kernel.  Even if machine I'm buying it for is running Windows.  However, when I bought this particular card, there were still very few dual-band WiFi-N cards on the market.

---

### Post by mick d on 2010-09-22
**You are right I don't wanna jump the gun too quickly, I will look at ebay and see about getting a cheap supported wireless card. That 600n wasn't cheap and I hate to see it obsolete but oh well if that's my biggest obstacle I will be happy. Thanks for the advice.**

---

