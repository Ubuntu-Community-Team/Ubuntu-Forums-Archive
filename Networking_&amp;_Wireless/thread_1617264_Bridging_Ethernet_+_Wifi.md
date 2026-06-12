---
title: "Bridging Ethernet + Wifi"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by docbrown on 2010-11-09
Hi

I have been trying to bridge my ethernet and wifi without any luck so far. I have found a few threads but havent found the anything suitable to my situation. I have also been able to share the internet from wlan0 to eth1 via iptables but this does not allow me to access the NAS connected to eth1 through my wireless network on 10.0.1.x subnet.

Heres my setup:


PC on Ubuntu 10.04 

  --->   wlan0: 10.0.1.11 --->   Gateway 10.0.1.1
                                --->     eth1: 10.0.2.11 --->   NAS 10.0.2.21

I understand that i need to set up a bridge to aggregate the two network interfaces, but how do i set up wlan0 to continue using 10.0.1.1 as a gateway, and maintain the WPA2 key etc, rather than becoming an access point as described in this post? 

[https://help.ubuntu.com/community/BridgingNetworkInterfaces](https://help.ubuntu.com/community/BridgingNetworkInterfaces)

From what i understand, that post explains how to use eth0 to connect to the internet, and ath0 as an access point for other computers in the local network. What i am trying to achieve is the opposite: wlan0 connects to gateway, eth1 connects to local network. Is this possible? 

Could someone please explain what i would need in /etc/network/interfaces ?

Thanks, really appreciate it.

---

### Post by docbrown on 2010-11-10
Ok after further searching I have found that wlan0 cannot be bridged while in managed mode.

I am now thinking of setting up the pc as a router per the instructions in this guide:
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

My wifi gateway is an Airport Extreme which supports wireless network extension via WDS.

If I set up an Ubuntu router, will it be able connect and extend the wifi network with WDS?

Any thoughts would be appreciated.

---

