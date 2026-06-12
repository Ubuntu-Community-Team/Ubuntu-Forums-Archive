---
title: "Wireless connection problems upon startup - wireless networks device not ready"
date: 2012-02-02
forum: Networking &amp; Wireless
---

### Post by oli.kerr on 2012-02-02
Hello all,

I have a fairly tedious problem with plenty of tedious specifics to ask your help for.

I have just bought a Lenovo G570 from which I am dual booting windows 7 and Ubuntu 11.10. Upon booting windows 7, the wireless engages with the network immediately and with a very strong connection. However, upon booting Oneiric Ocelot my wireless does not connect at all giving the message 'wireless networks device not ready' and only does connect after being in a hibernation state for around 30mins.

When a wireless connection is established it is very patchy, breaking off every 10minutes or so and is not as speedy as windows 7.

Couldn't find anything specific elsewhere on the forums...

Thanks in advance,
Oli

---

### Post by praseodym on 2012-02-03
Hi,

please show

```
lspci -nnk | grep -iA2 net
iwconfig
lsmod
rfkill list
```
Did you check the BIOS settings?

---

