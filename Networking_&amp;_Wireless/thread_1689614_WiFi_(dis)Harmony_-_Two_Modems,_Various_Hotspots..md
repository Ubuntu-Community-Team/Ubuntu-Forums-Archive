---
title: "WiFi (dis)Harmony - Two Modems, Various Hotspots."
date: 2011-02-17
forum: Networking &amp; Wireless
---

### Post by Sean Moran on 2011-02-17
My trusty laptop; a Compaq Presario CQ60; has a builtin Atheros AR5001 wifi adaptor, and last year before I understood that aircards require a slot for a SIMM chip, I accidentally purchased a ZyDAS ZyXEL G-202 adaptor that looks quite like a typical aircard (without the slot for the SIMM), and attached to a nice little USB socket on the end of a couple of metre long cables, and hung out the window over the balcony, I can pickup reception from quite a few more hotspots than via the Atheros which is limited geographically by the needs of the user to view the laptop screen without too much glare or sunlight, at a desk conducive to operating a keyboard.

The Atheros usually picks up two or three wifi hotspots as well as a couple here in this hotel.  The ZyXEL, when positioned in the right spot out on the balcony, seems to pick up all those hotspots, as well as half-a-dozen others across the road and all the way to the department store 100m up the road.

Thinking intuitively, it makes sense to connect BOTH modems to the strongest available hotspot and run them in tandem, either to two different servers, (whichever is strongest at the time from each point of receival), or often to the same server.  All these connections have their ups and downs though, and it's hard to tell for sure what might be causing the significant changes in download speeds, - sometimes as high as 800KB/S and sometimes as low as 800B/S, usually around 20-30KB/S - but it seems fairly clear by now that running two connections in tandem to the same server causes some serious conflicts, and the whole show almost comes to a stop.  If one connection is dropped, the remaining connection seems to quickly resume at the expected pace.

Running two connections to two different servers remains an unknown, because I can't seem to find two reliable servers at the same moment from here, but there doesn't seem to be the same conflict with two connections to TWO servers, as there is when I try to run two connections to the SAME server.

I write this thread to ask if someone might have some expertise on wifi and how Linux deals with it, to determine which is best: one modem at a time, or one server at a time: or maybe some configuration changes that might enable my system to work with both wifi adaptors without conflict.  Practical and theoretical replies would both be much appreciated if you can help my limited understanding of the essence of wifi.

---

### Post by Hilarie on 2011-02-17
Blind leading the blind here, but it might just be a simple case of radio interference, I know my wifi goes wonky if me and and another are to close while connecting to a weak connection

---

### Post by Sean Moran on 2011-02-17
> **Hilarie said:**
> Blind leading the blind here, but it might just be a simple case of radio interference, I know my wifi goes wonky if me and and another are to close while connecting to a weak connection
That's a good point that I haven't considered.  I do try to keep the mobile phone a few metres away from the modem/s to clear the way for the wifi, but I've been concerned more with what might be happening at the transmitter or receiver ends to do with how the system deciphers the radio signal, rather than the conflict of radio signals themselves.  It should have been obvious to me.

I hadn't thought about how it might be to have a single server 50 metres away trying to transmit the same data to two modems only a couple of metres apart.  (I might need to invest in another couple of cables to extend the distance of the ZyXEL another couple of metres away and see if that inproves reception.)

I'll go for a shopping trip tomorrow and test things out with both modems twice as far apart.  I assume that a USB modem won't suffer from 4 metres of cable, seeing it's all 5 volt and not likely to lose anything significant over that distance. In any case, USB cables won't break the bank.

Thanks Hilarie.

---

