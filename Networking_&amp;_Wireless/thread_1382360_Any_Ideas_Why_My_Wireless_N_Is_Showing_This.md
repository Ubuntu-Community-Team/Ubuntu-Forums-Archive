---
title: "Any Ideas Why My Wireless N Is Showing This:"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2010-01-15
I'm running UNR 9.10 on an Asus EeePC 1005HA connected to a D-Link DIR-655 802.11b/g/n router. In the router settings I *only* have it transmitting in "n" mode and am using WPA2 (AES). When I run "sudo iwlist scanning," it gives me this:
```

Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s

```
On two lines, just like that. Never seen this before... I thought n was supposed to give me 300 Mb/s?

---

### Post by moore.bryan on 2010-01-16
Nevermind... I researched a little more and found that D-Link is not going to support 5ghz/300mbs in this round of firmware and OpenWRT doesn't play well with the DIR-655 for "stupid" reasons.

Thanks, any way.

---

