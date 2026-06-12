---
title: "Any tips on getting power to a Netgear WG511 PCMCIA card?"
date: 2005-02-04
forum: Networking &amp; Wireless
---

### Post by Chris in Texas on 2005-02-04
Ok,

Now that I've finally gotten my software woes out of the way (hopefully), I am moving onto my next painful step of entering the world of Ubuntu.

I installed ndiswrapper (probably one of the more difficult things I've ever done- a dyslexic reading lines of code is not a pretty sight).  The drivers are loaded and present. That part is great.

Unfortunately the card will not work.  It does not seem to have any power.  I read on the sourceforge website until my head hurt.  This seems to be the best I could find:

>  For some cards it is enough to change/add setting in /etc/ndiswrapper/<driver>/*.conf files to 1. For example, SMC cards have a setting 'EnableRadio|0' which means radio is off. Change that line to 'EnableRadio|1'. Other cards may have other settings. 

I tried doing this, but the computer won't allow me to.  Any other tips on how to power up the card?  

This is a Toshiba Terca 8000 PII and I'm trying to power up a Netgear WG511 (made in China) card.

Thanks,

Chris

---

### Post by ktjensen on 2005-02-04
why did you need to use the ndiswrapper?  My NETGEAR WG511T card was completely recognized by the laptop.   I still can't connect, but my 802.11G network is seen.  Someone else mentioned I may need to do a STATIC address not a DHCP address.

---

### Post by Chris in Texas on 2005-02-04
I tried the card as is but it wouldn't recognize it.  I appear to have the "Made in China" card that doesn't seem to work with anything.  I couldn't even get the Netgear drivers to work.  After loading a different set of drivers the wrapper worked fine, but I still don't have any power going to the card.

---

