---
title: "Creating a router!"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by Kazagistar on 2009-08-31
I am attempting a rather complicated project related to wireless networking, that is just beyond my current abilities (the learning zone :P).

This is the situation; I am at a dorm room, and I have 3 computers: one desktop, one laptop, and one recently purchased EeeBox (a small quiet desktop). All 3 have wireless cards, and all 3 run Ubuntu, but here is some info on the hardware in my EeeBox, which is the most critical here:
```
03:00.0 Network controller: RaLink RT2860
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```

My goal is simple: I want to turn the EeeBox into a router, like those purchased in stores, but also let it be a server (I plan to eventually set up a VPN network to access it, but one thing at a time).

Basically, I want:
1) Wireless access, with some sort of opaque NAT. Simple Layer 2 bridging is NOT going to cut it (I need ip masquerade I believe).
2) WPA2, or at least some sort of solid encryption on the wireless data.

I have been reading various tutorials and instructions and hints on how to do this, but a lot of them are old, and only for a specific "aetheros" card that I don't think I have, and a lot are describing what looks to be just plain unsecured bridging, so I am worried... is what I want possible? Where should I go to learn more, and what method should I use?

My relevant skills: I can compile software from source (including the kernel, if I must), I have taken a networking course, I have had to fiddle with iptables once or twice, and I have been using Ubuntu and other linux distros intensively for 2 years.

---

### Post by mobilediesel on 2009-09-01
> **Kazagistar said:**
> I am attempting a rather complicated project related to wireless networking, that is just beyond my current abilities (the learning zone :P).

This is the situation; I am at a dorm room, and I have 3 computers: one desktop, one laptop, and one recently purchased EeeBox (a small quiet desktop). All 3 have wireless cards, and all 3 run Ubuntu, but here is some info on the hardware in my EeeBox, which is the most critical here:
```
03:00.0 Network controller: RaLink RT2860
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```

My goal is simple: I want to turn the EeeBox into a router, like those purchased in stores, but also let it be a server (I plan to eventually set up a VPN network to access it, but one thing at a time).

Basically, I want:
1) Wireless access, with some sort of opaque NAT. Simple Layer 2 bridging is NOT going to cut it (I need ip masquerade I believe).
2) WPA2, or at least some sort of solid encryption on the wireless data.

I have been reading various tutorials and instructions and hints on how to do this, but a lot of them are old, and only for a specific "aetheros" card that I don't think I have, and a lot are describing what looks to be just plain unsecured bridging, so I am worried... is what I want possible? Where should I go to learn more, and what method should I use?

My relevant skills: I can compile software from source (including the kernel, if I must), I have taken a networking course, I have had to fiddle with iptables once or twice, and I have been using Ubuntu and other linux distros intensively for 2 years.

[Untangle]("http://www.untangle.com") may be able to do what you want if the EeeBox also has ethernet. I can't find whether or not it supports wireless adapters. On the couple Untangle  boxes I set up it recognized every wired ethernet card I threw at it.

[Here]("http://forums.untangle.com/tip-day/2334-how-make-your-untangle-server-wireless-access-point.html") is a link to their forum about turning an Untangle server into an access point. It mentions Gutsy Gibbon but you might get what you need from there.

---

