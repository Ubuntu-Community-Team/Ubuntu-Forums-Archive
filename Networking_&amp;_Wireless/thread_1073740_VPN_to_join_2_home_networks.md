---
title: "VPN to join 2 home networks"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by bon_the_one on 2009-02-18
Hi all, 

I've had a look at the forums but most VPN seems to relate to connecting to a hosted account.

I have a few questions I wonder if anyone could help out with please?

First the scenario, I live in Spain, my best mate in the UK. His network is subnet 192.0.0.X, and mine is 192.168.0.x. We both have cable broadband, his on Virgin (UK), and mine on ONO (Spain).

We would like to create a VPN link, so that I may mount folders from his server onto mine, and he can mount folders from me onto his.

His server is Hardy running dhcp/dns etc, with 2 network cards in, 1 to the modem, one to the network switch for all his other house machines.

My server is Hardy running dhcp/dns etc, with 1 network card connected to a D-Link switch. My other machines are connected to the D-Link, and the D-Link's WAN socket connects to my modem. My D-Link copes with VPN pass-through.

My question are: 1) is setting a VPN tunnel over the public network viable in this configuration? 2) could anyone please point me to a good guide to learn how to configure this? 3) is it something I can configure locally here and via ssh on his, as tho he wants this to work his attention span is about 15 mins so I tend to have to do the hard work over shh!!

Many thanks in advance if anyone can offer any suggestions,
Yours,

Ian

---

### Post by veloce on 2009-02-24
> **bon_the_one said:**
> Hi all, 

I've had a look at the forums but most VPN seems to relate to connecting to a hosted account.

I have a few questions I wonder if anyone could help out with please?

First the scenario, I live in Spain, my best mate in the UK. His network is subnet 192.0.0.X, and mine is 192.168.0.x. We both have cable broadband, his on Virgin (UK), and mine on ONO (Spain).

We would like to create a VPN link, so that I may mount folders from his server onto mine, and he can mount folders from me onto his.

His server is Hardy running dhcp/dns etc, with 2 network cards in, 1 to the modem, one to the network switch for all his other house machines.

My server is Hardy running dhcp/dns etc, with 1 network card connected to a D-Link switch. My other machines are connected to the D-Link, and the D-Link's WAN socket connects to my modem. My D-Link copes with VPN pass-through.

My question are: 1) is setting a VPN tunnel over the public network viable in this configuration? 2) could anyone please point me to a good guide to learn how to configure this? 3) is it something I can configure locally here and via ssh on his, as tho he wants this to work his attention span is about 15 mins so I tend to have to do the hard work over shh!!

Many thanks in advance if anyone can offer any suggestions,
Yours,

Ian


VPN is still in the realm of the dark arts.

I would suggest you install separate firewalls from your server - if you use IPCop you can use any old pentium with 64Mb and 500Mb of disk.  IPCop has a built in VPN which I have managed to get working in a virtual environment.

---

