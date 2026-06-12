---
title: "Packet Loss with Atheros"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by doktoreas on 2009-05-03
Hello folks,
I just installed latest Ubuntu inside an Intel Mac Mini. All is fine except for wifi where I have got a 23% of packet loss.
If I put my laptop (using 9.04 too) in the same position of the Mac, to check for signal strength, I have got 0% of packet loss.

Info:
> 02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
21 packets transmitted, 16 received, 23% packet loss, time 24153ms
rtt min/avg/max/mdev = 53.262/55.703/80.203/6.346 ms


Using a brand new Ubuntu 9.04 with default installation.

Thank you very much
Luca

---

### Post by jhellan on 2010-05-01
I wrote the following, before noticing that the original post was 1 year old:

| Me too. Well - more like 10%, but that's also catastrophic.

| Same result with ath5k driver, madwifi snapshot 2010-03-25 and madwifi snapshot 2009-09-29.

| Same result with 3 different Atheros cards, 2 mini-pci and 1 external.

Jaunty and Karmic were OK, but got this with Lucid.

---

