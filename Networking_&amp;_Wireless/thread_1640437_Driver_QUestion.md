---
title: "Driver QUestion"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by badnaam on 2010-12-07
My wifi adpater (built into HP laptop) is a intel wifi link 1000 series (b/g/n I think). Looking at some other resources it seems iwlwifi driver is the recommended driver for this card? however it is currently using iwlang. 

I am constantly experiencing dropped connections with my belkin g router and I am wondering if changing the wireless adapter driver might help, even if it doesn't what is the best driver for this card?

Thanks!

---

### Post by chili555 on 2010-12-07
I believe iwlwifi is the name of a suite of drivers for a whole range of Intel cards. One of the drivers is *iwlagn*. My laptop uses another member of the family, *iwl3945*. As far as I know, *iwlagn* is the best and only native driver for the newer n-capable cards.

You might try installing linux-backports-modules-compat-wireless. It has a newer iwlagn in it. If there is something systemically wrong, a newer driver generally won't fix it.

What are your symptoms?

---

