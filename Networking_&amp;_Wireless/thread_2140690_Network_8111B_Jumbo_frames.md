---
title: "Network 8111B Jumbo frames"
date: 2013-04-30
forum: Networking &amp; Wireless
---

### Post by elite1967 on 2013-04-30
Hi, 
Using Ubuntu 12.10 with Realtek 8168B/8111B network card @ Giga Ethernet.

I am trying to set the jumbo frames of my network card to 9000.
But It does not seem to work:

here is what I do:
```
sp@SP-SERVER:~$ lspci | grep Eth
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
sp@SP-SERVER:~$ sudo ifconfig eth0 mtu 9000
SIOCSIFMTU: Invalid argument
sp@SP-SERVER:~$

```

Only 4000 works (not even 5000):
```

sp@SP-SERVER:~$ sudo ifconfig eth0 mtu 5000
SIOCSIFMTU: Invalid argument
sp@SP-SERVER:~$ sudo ifconfig eth0 mtu 4000
sp@SP-SERVER:~$

```

What I am doing wrong?
thanks

---

### Post by Slim Odds on 2013-04-30
Have you checked the documentation for the card?

Wikipedia says this about "Jumbo Frames": "Conventionally, jumbo frames can carry up to 9000 bytes of payload, but  variations exist and some care must be taken using the term."

---

### Post by elite1967 on 2013-04-30
> **Slim Odds said:**
> Have you checked the documentation for the card?

Wikipedia says this about "Jumbo Frames": "Conventionally, jumbo frames can carry up to 9000 bytes of payload, but  variations exist and some care must be taken using the term."

Hi,
thanks for your reply.
You mean that it's a hardware limitation?

There is no way to check on Realtek website as the datasheets are reserved for the developers/partners.

---

### Post by Slim Odds on 2013-04-30
> **elite1967 said:**
> Hi,
thanks for your reply.
You mean that it's a hardware limitation?

There is no way to check on Realtek website as the datasheets are reserved for the developers/partners.
Yes, I assume that is what it means.

---

