---
title: "Wireless working with 8.04 LiveCD, not after install"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by BallisticBanana on 2009-07-04
Hi there,

I've picked up a nice, cheap PC with a Netgear WPN311 PCI wireless card installed and am setting it up as a server-of-sorts.

My problem is this: when using the 8.04 LiveCD I have no problems at all connecting to the internet via my Netgear wireless router (using WPA security), but after installing to the hard drive (80Gb - full/clean install) I cannot connect the the router at all.  

I will try another clean install from the LiveCD - if anyone can make any suggestions it would be much appreciated.

Thanks,

---

### Post by computer13137 on 2009-07-04
Hmm, I can't think of any reason why that would happen.  I do have one question for you - is there a particular reason you are using 8.04 and not 9.04?  In my experience, 9.04 has far superior support for wireless networking...

Could you please paste us the output of the following commands, maybe even do it once in a real environment and again in a live environment?  They may help us to see the difference.

```
lspci
``````
iwconfig
```Also what do you mean by "doesn't connect"?  Does the hardware not even show up in the network manager, or does your network just not show up?

Cheers,
Kirk

---

### Post by BallisticBanana on 2009-07-05
Hi there,

Thanks for the response - something bizarre must have happened (or more likely something I did) on the first install as it now appears to be working fine.

I'll be booting up again shortly so will check it again, but crossed fingers everything will be alright.

Thanks again for the response.

---

