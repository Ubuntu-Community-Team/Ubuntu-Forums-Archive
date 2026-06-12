---
title: "How to install/configure an ATI Rage 128 AGP?"
date: 2011-01-25
forum: Multimedia Software
---

### Post by claus on 2011-01-25
Hi,

a while ago I purchased a used PC with the above graphics card built-in, but I'm afraid to install the xorg driver. With my old PC, I always ran into problems when trying to install the proprietary Nvidia driver (read: no x-server). Is there a safe way to install & configure the driver for this card? What packages would I have to install via Synaptic?

I found a thread with the following values for xorg.conf:

Section "Device"
Identifier "Configured Video Device"
Boardname "ATI Rage 128" {Change this to your card name}
Busid "PCI:1:5:0" {This was detected before. Don't change yours}
Driver "r128"
Screen 0
Vendorname "ATI"
Option "MergedFB" "off"
EndSection

Would those values be ok?

TIA,

Claus

---

### Post by Mark Phelps on 2011-01-26
There are no proprietary drivers that will work with your card and recent Ubuntu versions, so don't waste time looking for any -- from AMD/ATI or anywhere else.

The system will install default open-source drivers.  If those work, you'll be OK but you may be limited in the visual effects they will support.

If they don't work, you'll have to use a different card.

And, you shouldn't need an xorg config file because newer Ubuntu versions work fine without one.

---

### Post by adz89 on 2013-04-04
[http://www.phoronix.com/scan.php?page=news_item&px=MTA5Mzk](http://www.phoronix.com/scan.php?page=news_item&px=MTA5Mzk)

Does this driver work?

---

### Post by oldos2er on 2013-04-04
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

