---
title: "Ubuntu Server 10.04 LTS not recognizing a new NIC card"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by tddian on 2011-08-11
Hi there!

I've been Googling this for a while with no success in the end…

I just reinstalled a fresh 10.04 LTS Server on a box we intend to use primarily as a web proxy (because we don't want people to use our legacy routers after that to circumvent this, we'll also have it act as full-on router).

The box originally had only its builtin NIC, so I plugged in a new D-Link DFE-530TX in there and rebooted.

The card isn't detected at any level: lshw -C network doesn't see it, nor lspci (of course), much less does it appear in /etc/network/interfaces.

Although the NIC's package boasts its Linux compat, it appears the drivers CD is just Windows (at any rate, I don't know how to add the drivers for it to my Ubuntu distro).

Can anyone please advise?

Thanks!

---

