---
title: "Internet only works with wireshark running"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by rj123 on 2009-03-02
Hi!

I have a strange problem. My internet only works when wireshark is running (capturing).
I'm using a usb wired network adapter.

Can anyone help me??

Thanks!

PS: With wireless works fine.

---

### Post by rj123 on 2009-03-02
Anyone??

---

### Post by The Cog on 2009-03-02
Out of interest, does it only work while the wrieshark capture is in promiscuous mode?

Makes me wonder of there's a problem with MAC address recognition.

---

### Post by rj123 on 2009-03-02
Yes I forgot to say. My network has MAC Address identification/filter . And I changed the MAC Address of the USB adapter to the same as the wireless adapter.
Can it be the problem, how I solve that??

---

### Post by The Cog on 2009-03-03
It may have something to do with it. You changed the MAC address to match what other MAC address - your own wireless adapter, or the access-point? 

But the only way I can imagine wireshark having anthing to do with it is if wireshark is putting the interface into promiscuous mode, which is why I asked that question. If so, it suggests that the adapter is having difficulty reconising packets sent to its own MAC address, but sees the packets when it's listening for packets to any address.

Maybe the routers ARP cache hasn't bee updated and its still addressing the packets to the original MAC address? You should be able to confirm that with wireshark.

---

