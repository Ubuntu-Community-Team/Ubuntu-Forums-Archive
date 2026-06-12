---
title: "Atheros mode master, how do i make mac filters?"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by haaglin on 2006-07-10
Hi. I have 2 wlan cards in my computer. ath0 to connect to a router an internet, and ath0 in master mode, to extend the range of the wlan. 
But how can i have encryption on that wlan? i want to have mac filters, so that only computers with the right mac adress can access the network. 
and another thing, as you can see below, it says Bit Rate 0kb/s. is there something wrong?

```

ath1      IEEE 802.11g  ESSID:"WLAN"
          Mode:Master  Frequency:2.412 GHz  Access Point: 00:0D:88:FA:52:D3
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=21/94  Signal level=-74 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by verbatim210 on 2006-07-10
your router/access-point
should have 2 functions
mac-filter and wireless encryption

using web interface to configure i am sure you can set up mac filter to your own specification.  mac filters come standard on home work office routers.

---

### Post by haaglin on 2006-07-11
> **verbatim210 said:**
> your router/access-point
should have 2 functions
mac-filter and wireless encryption

using web interface to configure i am sure you can set up mac filter to your own specification.  mac filters come standard on home work office routers.

Yes, but my ubuntu computer IS my wlan router.

---

### Post by verbatim210 on 2006-07-11
are you trying to save money using 2x wireless network cards as an access point?  this is a bad network setup.

i dont know how to configure linux as a router, sorry.  if anyone out there does, please shout :KS

---

### Post by haaglin on 2006-07-11
> **verbatim210 said:**
> are you trying to save money using 2x wireless network cards as an access point?  this is a bad network setup.

i dont know how to configure linux as a router, sorry.  if anyone out there does, please shout :KS

No its not bad network setup. My computer already acts as a wireless accesspoint(router). The reason i'm doing this is because my wlan is in 2 houses, and my laptops cant reach the router in the other house. so i'm extending the range using 2 wlan cards. and it works great, but i want mac filters, so my other neighbours cant connect to it.and its not to save money, i just had another wlan card that wasn't in use.

---

### Post by Sendervictorius on 2006-07-11
You need to set up your iptables firewall to accept the mac addresses you want to allow through.

This link shows how:

[http://www.cs.usfca.edu/~afedosov/netgreg/](http://www.cs.usfca.edu/~afedosov/netgreg/) 


> **haaglin said:**
> Hi. I have 2 wlan cards in my computer. ath0 to connect to a router an internet, and ath0 in master mode, to extend the range of the wlan. 
But how can i have encryption on that wlan? i want to have mac filters, so that only computers with the right mac adress can access the network. 
and another thing, as you can see below, it says Bit Rate 0kb/s. is there something wrong?

```

ath1      IEEE 802.11g  ESSID:"WLAN"
          Mode:Master  Frequency:2.412 GHz  Access Point: 00:0D:88:FA:52:D3
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=21/94  Signal level=-74 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

