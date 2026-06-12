---
title: "DVB-C many artifacts"
date: 2012-07-06
forum: Multimedia Software
---

### Post by Balr0g on 2012-07-06
Hi,

since I've upgraded my HTPC to Ubuntu 12.04 (64 bit) I thought it would be a good idea to reactivate my budget DVB-C card. It's a Technisat Cablestar 2 HD PCI card.

Chips: Philips TDA10023 / Mantis. It works out of the box after installing the linux-firmware-nonfree package.

The problem: TV is unwatchable - many block artifacts, stuttering. (SD and HD) 

It happens in Kaffeine as well as in Myth-TV. Background recordings show the same problem. The signal strength is > 80%, SNR is > 90%.

The cables are not the problem. For testing purposes I've plugged a stand-alone receiver in the DVB-C cards passthrough port - it shows a perfect picture.

I'd apreciate any ideas.

Regards,
Oliver

---

### Post by timbly5000 on 2012-10-01
Hi,

I have recently discovered a similar issue since moving to 11.04 64 bit in an i7 board. I am using a Technotrend S-1600 sat card and I experience a breakup every second or so on HD (can't say I notice anything on SD though).

The same card works fine for me in the previous PC (a P4-2.8G HT running Ubuntu 10.10 32 bit). Putting this 32bit Ubuntu disk in the i7 PC proves that the card can also work properly in the new i7 hardware. This points to there possibly being an issue with 64bit builds of the DVB drivers and/or utils.

Tim.

---

