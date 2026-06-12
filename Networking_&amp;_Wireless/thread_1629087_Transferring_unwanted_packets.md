---
title: "Transferring unwanted packets"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by etienneh on 2010-11-23
Hi everyone,

I use Ubuntu at my university and have had lots of trouble the last two days. The university's wireless access points have been upgraded to a newer software version and me and many other Linux (mostly Ubuntu) users are having the same problem:

Since the update, our systems appear to be transferring lots of unwanted packets. In a few hours, without using the net, my system transferred over 450MB of data, the network admin told me. Since the network admin doesn't seem to know what to do, I tought I'd ask around here.

I have attached a screenshot of wireshark. I receive at least 100 to 200 such LLC (Logical Link Control) packets per second destined from one MAC-adress to another, neither of which is mine, both always belong to some access point are some other hardware.

I have tried blocking the MAC, but then I can't use the network anymore on this access point, and since all of them are behaving like this, it doesn't help. Firewall didn't help either, as this is a very low level protocol.

Any ideas? After a few minutes, I can't even access the net anymore.

---

