---
title: "Airlink 101 AWLH6070 150N - rt2860 driver"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by karl_210 on 2010-06-14
I use to have problems getting my wireless card to connect to any network on ubuntu. I discovered that I needed to change my encryption mode from Auto to AES or TKIP on my router. After I did this I was able to connect to my network with full wireless n support. I am using a d-link DIR-615 wireless n router.
 
So far I know this works perfectly on 9.04-10.10 alpha.

---

### Post by TBerk on 2010-06-15
A couple of things; 

1) I'm using the Airlink PCI based RT2860 chipset card in my system. 

2) I default to WPA2 and AES on the Router.

3) I had been compiling my own Ralink support  prior to installing 10.04, but out of the box this OS version supported my wifi card. (Even from the LiveCD!)

4) I've been looking into verifying things and I see from my Network Manager that my connection speed seems to be 54Mb/s.  (This is to a Dual Band draft N router with 2.4Ghz and 5Ghz frequenc6 support.)

What I was sort of expecting was something that showed 150, perhaps 130 instead of 54.

What I'd like to get out of this would be a better throughput, something I could demonstrate the 3.0Mbs that ATT DSL says the line is provisioned for through the Router to my Desktop System.

I'm wondering if recompiling and/or altering settings would be or any use.


TBerk

---

