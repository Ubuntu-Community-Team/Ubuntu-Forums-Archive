---
title: "HP G42 Wireless Issues"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by ShawnCowles on 2011-02-06
Hi everyone. I've been using Ubuntu on my desktop for a few months now and I'm really enjoying it. I bought an HP G42 today and installed 10.04 on it, and as expected the wireless doesn't work.

I searched around and couldn't find any helpful information for this model.

No wireless connections are present in the Network Connections manager, the "toggle wifi" button seemingly has no effect (the led stays a constant orange).

I presume its a driver issue, but that's as far as I know.

Can you point me at any helpful commands / resources?

I know my way around a command-line, so you don't need to explain any of that to me.

Thanks in advance.

---

### Post by RedSingularity on 2011-02-06
Whats your ifconfig output?

---

### Post by ShawnCowles on 2011-02-06
It shows information for eth0 and local loopback, no wireless.

according to lspci:
02:00.0 Network Controller: Broadcom Corporation Device 4727 (rev 01)

EDIT: I just tried an physical connection, no luck there.
ifconfig for eth0 shows 399 RX packets and 18 TX packets, but pinging a computer on my own network gives the reply: "connect: Network is unreachable"

EDIT2: Ok, so I did some more looking this morning for information about just the card and found that just about everything required an internet connection.

I downloaded and installed drivers for my wired card from realtek and once I was online the Hardware Drivers utility handily downloaded the necessary wireless drivers.

Thanks for your time RedSingularity

---

