---
title: "another karmic wifi issue *different*"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by Jay105 on 2010-01-07
hey guys

finally took the plunge and upgraded my ubuntu studio to karmic from jaunty. i seem to be experiencing a problem many have, being that my wifi card (edimax) which worked on my previous distro is now not working at all. ive done a lot of research and found the problem seems to mainly be with broadcom cards, and have tried a number of things relating to those that have worked for others, with no luck.

my problem seems to be not that the drivers wont activate or anything like that, my problem is that under hardware drivers NOTHING appears at all. i have no drivers present, where most people are talking of 3. i have not found anyone else with this problem.

my problem is compounded in addition by not being about to use a wire connection at all. 

any help would be greatly appreciated :) 

james

---

### Post by gordintoronto on 2010-01-07
Which Edimax?  According to this:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax#PCI) 

there are several Edimax adapters, which are very different.

From a terminal you can use 
lspci
or
lsusb
to see the detailed identification of your Edimax.

Do you have a network icon?  Have you set up a wireless connection before?

---

### Post by Jay105 on 2010-01-08
for lspci its telling me the network controller is an Ralink RT2561/RT61 802.11g PCI. is this what your after? 

no network icon at all, no LED flashes from PCI, just nothing at all. my previous distro accpeted it no problem, no install, no configuration, plugged it in and recognized and worked from the outset.

thanks


EDIT: downloaded appropriate driver from internet and put on the karmic machine with usb flash drive, but when i open the configure shell script it flashes up for maybe half a second and disappears again. FRUSTRATING!  

thanks

---

### Post by clhsharky on 2010-01-08
HI Jay105

I have that same card in my desktop with Ubuntu 9.10, it is supported. Never had to install anything, I have had to restart my computer for every thing to be recognised properly,maybe 3 or 4 times since Karmic install. Couldn't tell if router, card or Karmic was the problem. Hope that helps.

Sharky

---

