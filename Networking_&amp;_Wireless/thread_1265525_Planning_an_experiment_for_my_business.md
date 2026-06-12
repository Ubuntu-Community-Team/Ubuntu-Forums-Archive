---
title: "Planning an experiment for my business"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by theozzlives on 2009-09-13
Suppose I have two computers I want to share users, files, and Broadband. computer 1 has two NICs (ETH0 and ETH1). computer 2 has 1 NIC. I have Broadband connected to ETH0 of computer 1. I have a crossover cable going from ETH1 of computer 1 to ETH0 of computer 2. I have a static IP.

I'm thinking I world have to setup computer 1 as a DHCP server, what's your thoughts?

Also, would that change is the IP was Dynamic?

---

### Post by Iowan on 2009-09-13
You *should* be set up static addresses (meaning you wouldn't need to set up DHCP server... but you could). Setting up DHCP for a single computer seems like unnecessary work - unless you anticipate expanding the network later.
eth0 and eth1  (on computer 1) should be in different subnets.

---

### Post by theozzlives on 2009-09-14
> **Iowan said:**
> You *should* be set up static addresses (meaning you wouldn't need to set up DHCP server... but you could). Setting up DHCP for a single computer seems like unnecessary work - unless you anticipate expanding the network later.
eth0 and eth1  (on computer 1) should be in different subnets.

OK, I was just running a scenario in my head. In the old days I would just run a 10-base-T with a terminator on each end, since then, I've been using a router. Since I can make my own crossover cables and have NICs a-plenty, I was trying to think of a way to keep customer costs low with a high profit for me. For more than 2 computers, it wouldn't be feasible. May as well get a router and use the built-in DHCP.

---

