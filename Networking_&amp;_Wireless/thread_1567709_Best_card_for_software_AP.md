---
title: "Best card for software AP?"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by Fafler on 2010-09-04
It's been a couple of years since the last time i had a software access point, but i'm getting tired of my current access point and as i have a home server running 24/7, already acting as router etc. it seems like a good choice to upgrade it.
Whats the best card for a software AP? Is madwifi still the best choice or have other drivers come up to par?

Either PCI or PCIe and it has to support B, G, and N with 2 or 3 external antennas.
Could i by the way buy a antenna like this [http://cgi.ebay.com/800mW-USB-WiFi-Adapter-802-11G-B-N-18dBi-Yagi-Antenna-/280557674135?pt=AU_Networking&hash=item41528a5e97](http://cgi.ebay.com/800mW-USB-WiFi-Adapter-802-11G-B-N-18dBi-Yagi-Antenna-/280557674135?pt=AU_Networking&hash=item41528a5e97)
and connect it to one of the antenna connectors and use it with 2 normal antennas inside the house to give better coverage in my garden or does the card expect 3 of the same antennas?

I am, by the way, running Debian Squeeze on the server.

---

### Post by BkkBonanza on 2010-09-04
I don't know if it's the best but I have had good success with an Atheros Ath9k card and current drivers. It works with hostapd and I have one in my mini-itx Ubuntu router on a tiny miniPCIe card. There seems to be lots of them cheaply available on eBay, where I got mine. 

Several of the older cards supported by hostapd seem to be hard to find now and they wouldn't have N support.

---

### Post by Fafler on 2010-09-05
Can you link to a specific card? mini PCIe is alright, as i can always stick it in a adapter.

---

### Post by BkkBonanza on 2010-09-05
I think this is the one I got,

[http://cgi.ebay.com/New-Atheros-AR9281-802-11N-WiFi-over-AR5008-2-antenna-/230444987926?pt=LH_DefaultDomain_0&hash=item35a7977616](http://cgi.ebay.com/New-Atheros-AR9281-802-11N-WiFi-over-AR5008-2-antenna-/230444987926?pt=LH_DefaultDomain_0&hash=item35a7977616)

with laptop style internal antennas for about the same price a year ago. Same seller I believe. But he also sells them without antennas, and you would need little adapter cables to hookup external ones. I put these little antennas inside my mini-itx case and that worked ok. I didn't do distance tests.

I have no idea if that's the best one. There are several AR92xx models around and I suspect that there is a newer model. I saw one that has 3 antenna connectors.

See this page for Atheros chipset support,
[http://linuxwireless.org/en/users/Drivers/ath9k](http://linuxwireless.org/en/users/Drivers/ath9k)

And then maybe look at Atheros site for chipset info about best N modes. I'm not sure which is better, maybe AR9285. The models #s are confusing as some of the AR50xx models seem to be the same.

When I first installed I had to use the backport drivers but it seems new kernel versions have native support. I have it running on 10.4 now.

In hostapd you set driver=nl80211
If you need an example hostapd.conf file let me know.

---

