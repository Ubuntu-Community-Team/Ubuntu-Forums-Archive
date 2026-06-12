---
title: "iwl3945 on Vaio VGN-UX17GP default antenna wrong"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by owenspa on 2009-03-30
I hope this helps someone else.

Running kubuntu 8.04 I couldn't get the wireless (Intel Pro/wireless 3945abg/bg) to work consistently outside of a 2m range.

After trying heaps of suggestions and installing "linux-backports-modules-hardy-generic", I noticed the "antenna" parameter.  By default this
is set to 0 to enable both the main and auxiliary antennas.

The Sony VAIO VGN-UX17GP doesn't have an auxiliary antenna.

So I set the iwl3945 module parameter "antenna" to 1 to enable
the main antenna only.  Now I can get wireless access through out the
house and into the yard.

PS: to permanently set the driver parameter, create /*etc/modprobe.d/iwl3945* to contain -

```
alias wlan0 iwl3945
options iwl3945 antenna=1
```

---

