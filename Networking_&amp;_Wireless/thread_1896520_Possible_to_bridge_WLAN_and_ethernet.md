---
title: "Possible to bridge WLAN and ethernet?"
date: 2011-12-17
forum: Networking &amp; Wireless
---

### Post by koma77 on 2011-12-17
I want to use my old laptop as a kind of bridge between a WLAN and a regular ethernet LAN.

So, basically, all traffic on the LAN should be visible on the WLAN and vice versa. The two networks should be connected as by a switch.

Is it possible to do this?

If it was two ethernets I'm sure it would, but with one WLAN and one ethernet LAN?

---

### Post by squaregoldfish on 2011-12-17
I can't think of any reason why not - they're both just network connections after all. You'll just be using eth0/wlan0 instead of eth0/eth1.

Steve.

---

### Post by koma77 on 2011-12-17
That sounds promising!

So, what should I look up? Bridging? Or is there another term for what I'm trying to do?

---

### Post by koma77 on 2011-12-17
I guess my concern is that a WLAN is a bit different. With WPA enabled any station has its unique encryption with the access point. So, only traffic directed to the laptop-acting-as-a-bridge would then be possible to decrypt and send onto the ethernet.

And since the laptop-bridge ideally should be transparent to the network, I'm not sure how that will work...

---

### Post by squaregoldfish on 2011-12-17
The WPA stuff is at a different level to the networking that you're thinking of. All the encryption happens at the driver level, and what the Linux networking stuff is presented with is a TCP/IP connection the same as any other.

All you're doing with a bridge is saying 'forward stuff from the IP address on this network connection to the IP address on that network connection'. Both connections have an IP address, so it's all good!

Steve.

---

