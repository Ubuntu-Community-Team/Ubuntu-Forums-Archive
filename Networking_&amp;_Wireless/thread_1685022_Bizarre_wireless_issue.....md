---
title: "Bizarre wireless issue...."
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by restofactor on 2011-02-10
Hi there,

Newbie to the forum here ):P

I have a bizarre wireless issue. My wireless card works well wherever I go but yesterday I went to a client and my wireless card does not work at the client. I will be at the client for a few weeks to come. They have a wireless Internet access point for consultants to use. My card does not connect to the access point and it also does not connect via the wireless APN created on my mobile phone whilst at the client. When I go back to the hotel or anywhere else, everything works fine (including the APN via my mobile).

I got given a wireless USB card and I plugged it in and everything worked fine via the Wireless USB. For the moment I am using the wireless USB but it frustrates me that my on-board wireless card does not work here at the client. What is even more strange is that it can see the networks via "iwlist scanning" but it does not connect to it. The wireless access point is open and does not have any strange encryption or MAC address filtering configured on it.

Could it be due to some strange signal interference in the air in this area? Maybe a manufacturers fault with the card as the Netgear USB card works fine?

OS => Ubuntu 10.10 (Gnome)
Hardware => Dell Inspiron 15R Laptop
Wirleess card according to lspci => 12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)

I have seen the Broadcom thread and I tried re-installing the drivers etc. but it does not solve the problem.

Any ideas?

---

### Post by restofactor on 2011-03-19
For anyone interested, this turned out to be my Broadcom driver not being compatible with the Wireless-N standard. The access near where I was sitting was configured to utilise the N standard.

---

