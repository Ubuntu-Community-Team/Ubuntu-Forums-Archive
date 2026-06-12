---
title: "Altheros AR2413+WPA as AP. Is that possible?"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by PryGuy on 2009-02-15
Good day all of you!
I have a server that runs Ubuntu 8.10 Server and I have to set up a wireless AP on it. lspci | grep Atheros says: ```
00:10.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
```I honestly couldn't find a step by step howto on this question. Madwifi says card is not supported if I put it into Master mode. Wext does not work either. Should I use ndiswrapper?

---

### Post by kevdog on 2009-02-15
The ability to go into Master Mode depends on your driver.  I believe 2413 uses the ath5k driver which can not do Master Mode.  Neither can ndiswrapper.  Madwifi can, however Im not sure if the 2413 can use a patched madwifi source as a driver.

---

