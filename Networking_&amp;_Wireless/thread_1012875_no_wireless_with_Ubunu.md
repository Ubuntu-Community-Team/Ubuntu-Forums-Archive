---
title: "no wireless with Ubunu"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by stickman51 on 2008-12-16
New laptop, Ubuntu 8.10; works online 100% if plugged into modem; cannot go online wirelessly unless I boot into Vista. Just now I posted this to a "local" group:

"I downloaded the Ubuntu 8.10 on Thursday and burned the Image CD and installed it on the new laptop. It runs 100% except that it cannot, apparently find my WIFI card.

And last night I plugged it into my modem (no router anymore; the modem does it all) and it was online instantly and downloaded and installed 189 updates no problem.

SO, it appears that Ubuntu 8.10 needs a driver for my wireless card. As John Jardine pointed out, it is:

05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg 
Wireless PCI Express Adapter (rev 01)
 Subsystem: AMBIT Microsystem Corp. Device 0428
 Flags: fast devsel, IRQ 17
 Memory at f0200000 (64-bit, non-prefetchable) [disabled] [size=64K]
 Capabilities: <access denied>
 Kernel modules: ath_pci

I'd prefer *not* to get a dongle; maybe I should just wait until some genius comes along and writes the driver? I'm sure I'm not the only user who would be very happy if somebody could do that."

Any chance of a driver being written? I'd be happy to provide all the info needed, from my new eMachines laptop.

---

### Post by ibutho on 2008-12-16
There already is a driver for that card. I have a laptop with the AR242x 802.11 card and Ubuntu (and Mint) is the only one that won't work out of the box. I tried openSUSE 11 (and 11.1rc), Fedora 10 and Mandriva 2009 and the card just works. Take a look at this [how to]("http://www.webdigity.com/index.php/topic,8202.0.Ubuntu+8.10+-+Atheros+AR242x+problems.html") and hopefully it may help resolve your problems.

---

### Post by stickman51 on 2008-12-16
> **ibutho said:**
> There already is a driver for that card. I have a laptop with the AR242x 802.11 card and Ubuntu (and Mint) is the only one that won't work out of the box. I tried openSUSE 11 (and 11.1rc), Fedora 10 and Mandriva 2009 and the card just works. Take a look at this [how to]("http://www.webdigity.com/index.php/topic,8202.0.Ubuntu+8.10+-+Atheros+AR242x+problems.html") and hopefully it may help resolve your problems.

THAT looks hopeful, ibutho! Working on that now. Will advise.

---

### Post by stickman51 on 2008-12-16
ibutho, he says "3) We need to install WICD which can be configured in order to use the WEXT driver. Go to Settings > Repositories > Third Party Software > Add and add the following line :" but I've been into Linux for a few days only, so please, how do I find that SETTINGS dialog box?

---

### Post by Ayuthia on 2008-12-16
> **stickman51 said:**
> ibutho, he says "3) We need to install WICD which can be configured in order to use the WEXT driver. Go to Settings > Repositories > Third Party Software > Add and add the following line :" but I've been into Linux for a few days only, so please, how do I find that SETTINGS dialog box?
That is in the Synaptic package manager.  I am currently in KDE so I can't remember where that application is located in the menu items.

---

### Post by stickman51 on 2008-12-16
GOT IT! Problem solved; I'll start a new thread "SOLVED: Ubuntu wireless" so everyone might benefit.

THANKS TO ALL OF YOU!!

---

