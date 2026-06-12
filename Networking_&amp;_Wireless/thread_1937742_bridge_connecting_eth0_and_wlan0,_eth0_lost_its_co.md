---
title: "bridge connecting eth0 and wlan0, eth0 lost its connection"
date: 2012-03-08
forum: Networking &amp; Wireless
---

### Post by dengn on 2012-03-08
hi,

I am setting my Linux as an wireless AP and i've already made the hostapd working.
Then I've followed the instructions of building a bridge between eth0 (wired connection) and the wlan0 (wireless connection that I will share with other nodes) by using brctl.
Then it works well in the client side, I've got the connection from eth0 and shard the internet from it, but in the AP itself, it losts its connection of internet. Basically, I found out that when I did "brctl addif br0 eth0" to add eth0 into the bridge, the connection was immediately lost.
I've also set an IP address for br0, by DHCP of gateway.

Do you have some solutions for that?

---

### Post by Hulkiedulkie on 2012-03-09
Are you accessing the internet through eth0? If so it should not be bridged with wlan.

Do you have 2 wired network adapter or just 1? If there is only 1 you should not bridge it with wlan, just enable forwarding and it will work.

---

