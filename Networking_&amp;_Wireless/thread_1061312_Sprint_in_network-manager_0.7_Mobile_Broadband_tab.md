---
title: "Sprint in network-manager 0.7 Mobile Broadband tab"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by CalaverX11 on 2009-02-05
I see AT&T and T-Mobile. When will Sprint be available? How do I create a native connection with my Sprint Novatel 5720 EVDO card?

Don't bother pointing me to scripts or pppd or kppp, I've already done that. I don't want to use kppp or pppd scripts, I want it native in network-manager 0.7 like it's supposed to be already. First I want to know if it's possible, and if not, when it will be. I must be parsing my searches on Google wrong, because no matter what I enter and how deep I search, I keep getting thrown back to launchpad's network-manager PPA, and no matter what version I "upgrade" to from the PPA, I get the same results. No Sprint option, no Novatel 5720 CDMA EVDO.

Anybody?

---

### Post by CalaverX11 on 2009-02-06
Anybody?

---

### Post by CalaverX11 on 2009-02-06
The good news is, the "Auto Mobile Broadband" connection shows up in network-manager when usbserial is loaded. I still have no idea how to get it to recognize the card without usbserial. Modprobe usbserial with the vendor and product IDs gets it to recognize, but because it's connecting at USB speed instead of the "airprime" speed (which no longer exists...wtf?), it's much slower than it is in Windows.

How do I get the "airprime" or whatever it's called nowadays to load so the card is recognized on boot instead of having to add modprobe usbserial to my modules file?

---

