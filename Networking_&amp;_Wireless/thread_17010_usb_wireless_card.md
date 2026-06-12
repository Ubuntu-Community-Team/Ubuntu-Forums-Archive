---
title: "usb wireless card"
date: 2005-02-25
forum: Networking &amp; Wireless
---

### Post by whittycat on 2005-02-25
I have just installed Warty and it's fine but I want to configure my Netgear MA111 wireless card. The modules prism2_usb and p80211 are both there so it should be easy. If I go to Computer->System Config->Networking and add
wlan0  the box gets a tick for a short while then the tick disappears.
I've looked in the forum and people seem to be saying that the only way of getting it to work are linux-wlan-ng or ndiswrapper but ndiswrapper itself says it is not supported and not recommended. So does Ubuntu support the prism2 usb wireless card or do I have to go to linux-wlan-ng? Oh and btw the hardware is ok cos it works in windows. 

Tony Sumner

---

### Post by archibald on 2005-03-04
use the ndiswrapper, it worked wonders with my ma111...
there are a few great guides to ndiswrapper setup on this forum...just search till you find them!!!
good luck

---

