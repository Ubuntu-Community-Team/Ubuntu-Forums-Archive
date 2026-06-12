---
title: "BCM43224 doesn't work on WPA2 Enterprise/Protected EAP (PEAP), MSCHAPv2"
date: 2013-02-05
forum: Networking &amp; Wireless
---

### Post by laurids on 2013-02-05
Hi,

I'm running Mint14 on a Macook Air (5,2).
The wireless card is Broadcom Corporation BCM43224 with wl driver. 

Everything works fine BUT on my college network, **WPA2 Enterprise/Protected EAP (PEAP), MSCHAPv2. **
Although I can join the network, the connection is extremely slow and unreliable (up to *minutes* to load a webpage).
I joined the network less then 5 minutes ago and according to iwconfig I get tons of Rx invalid crypt; and the number keeps increasing.
```

# iwconfig
          Rx invalid nwid:0  **Rx invalid crypt:3503**  Rx invalid frag:0
          **Tx excessive retries:212**  Invalid misc:0   Missed beacon:0

```
I have no problem whatsoever with any other kind of networks. 
I have no problem with WPA personal too at my place. 
Also, on Mint13 everything used to be fine.

May this be a bug? Any clue on that? Thank you!

---

### Post by laurids on 2013-02-08
Anyone? :(

---

### Post by bazooka2 on 2013-10-04
Hi,

I have the same problem. Have you managed to solve this?

I have tried with wl, b43 and brcmsmac in 3.11.3 and 3.4.64 but neither works.

---

