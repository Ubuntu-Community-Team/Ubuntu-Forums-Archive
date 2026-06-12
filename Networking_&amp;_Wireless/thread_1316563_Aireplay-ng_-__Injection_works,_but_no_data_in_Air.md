---
title: "Aireplay-ng -  Injection works, but no data in Airodump"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by fllash on 2009-11-06
Howdy all,
I've been using Ubuntu for a while now, and have run into a (somewhat minor issue) that has been bugging me. I understand that the kernel used in 9.10 has support for packet injection for **Intel 3945(a/b/g)**. Using Aireplay:
 - I can Authenticate with the target (and am notified of injection working, and recieve and ACK)
 
My problem is that when I proceed to inject packets using the "aireplay-ng -3" operator, I am notified that PPS injection is at 500, but the data count in airodump is not going up.

Just wondering if i am missing something.
Thanks for reading,
Josh.

---

### Post by malcolmmersham on 2009-11-20
i have the same problem, I am able to see BSSID's and when injecting deauth packets i can see MAC come up and go down but my data capture stays at 0

---

### Post by hardkorek on 2010-02-28
I have the same problem on Atheros chipset. I'm using acer aspire one, lspci identifies it as 
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

I can capture data packets in the same place from diferent device(maemo linux)

I have no problem in previous versions of ubuntu

---

### Post by hardkorek on 2010-03-01
In my case it was kernel issue, i boot from old one - 2.6.31-14 and air crack works like a charm. I already posted bug at launchpad.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530449](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530449)

---

