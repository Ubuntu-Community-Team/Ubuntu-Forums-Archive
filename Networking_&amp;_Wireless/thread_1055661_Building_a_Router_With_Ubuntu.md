---
title: "Building a Router With Ubuntu"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by ShinHadoken on 2009-01-30
What I would like to do is build a server/wireless router. Can anyone answer the following questions:

1. Can I configure a wireless card in the server to act as an AP, or would I have to get one?

2. How would I configure the server to act as a router, hardware _and_ software speaking?

3. How would I set up a RADIUS server for enterprise-grade WPA security?

Thanks in advance for the help!

- ShinHadoken

---

### Post by ShinHadoken on 2009-01-31
BUMP (in a polite way)

---

### Post by ShinHadoken on 2009-01-31
> **ShinHadoken said:**
> BUMP (in a polite way)
Ditto

---

### Post by ShinHadoken on 2009-02-01
Sorry, don't mean to be a nag here, but I understand how these things can get lost in the shuffle.

---

### Post by warchief_ryan on 2009-02-01
> **ShinHadoken said:**
> What I would like to do is build a server/wireless router. Can anyone answer the following questions:

1. Can I configure a wireless card in the server to act as an AP, or would I have to get one?

2. How would I configure the server to act as a router, hardware _and_ software speaking?

3. How would I set up a RADIUS server for enterprise-grade WPA security?

Thanks in advance for the help!

- ShinHadoken

1. Yes but not all cards can do it. You'll have to look up your cards chipset.  I think its a mode you have to put the card into like master mode or something, but the speed if I remember right your stuck at 11mbps.

2. Once you have the wireless working you can use iptables, I do it to share my connections works great.

3. Haven't tried or looked into it.

Theres alot of guides that can be found by googling "ubuntu wifi router" and check the ubuntu community docs.

---

### Post by ShinHadoken on 2009-02-01
Ok, sorry, I suppose I should've checked google first. Watching Super Bowl now, but I'll look into it l8er. Anyone else? =)

---

### Post by ShinHadoken on 2009-02-01
Actually, let me ask this question. Let's compare buying a dedicated hw router as compared to making one out of a PC with some additional NICs. The questions that come to my mind are:

1. Which is cheaper?

2. Which is easier?

3. For my wireless network, I will use WPA partnered with a RADIUS server, and I will NOT be broadcasting the ESSID. Which configuration allows this to happen easier, if at all (for the PC router)?

Hope this gets us somewhere. =)

- ShinHadoken

---

