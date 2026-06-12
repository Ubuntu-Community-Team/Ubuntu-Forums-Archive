---
title: "[SOLVED] Very slow wifi on Intrepid AMD64"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by Mintux on 2008-12-29
I upgraded from Hardy yesterday, and now my wireless connection is extremely slow - it takes forever to look up new pages. The packet loss is like 80-90%. If I disable the wireless connection and go hook up the wired NIC the connection is speedy as ever. I have a dual-core AMD Athlon 64, 2 gigs of RAM, and an internal DLink DWL-G520+ wireless PCI card, along with a Netgear 10/100 NIC. This is the relevant output of LSPCI:

```
01:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

```

I never had such problems under Hardy. There is a Windows XP-installation on the machine that I use for gaming, and it has no such problem. Neither has my Acer Aspire One which runs Hardy. The machines connect to the internet through a server running Hardy, which caches and provides DNS and DHCP.

---

### Post by Mintux on 2008-12-30
Bump. I see a lot of people have problems with network speed in 8.10, and I have even seen two or three with similar problems to mine. However, no good answers yet.

---

### Post by Mintux on 2009-01-01
Bump again. Intrepid has been out for like 3 months - is there really nobody who has any idea what may be going on?

---

### Post by Mintux on 2009-01-01
Chucking out Network Manager and installing Wicd instead seems to have resolved the problem. The wifi connection is fine now - no more packet loss.

---

### Post by n2iw on 2009-01-02
> **Mintux said:**
> Chucking out Network Manager and installing Wicd instead seems to have resolved the problem. The wifi connection is fine now - no more packet loss.

How do you "Chuck out network manager and install Wicd"?

---

