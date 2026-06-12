---
title: "ThinkPad x201s - wireless connects but no internet"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by ch33ky on 2011-06-17
Hi,

I'm having some wireless issues on my ThinkPad x201s (running Ubuntu Natty 11.04) which I hope someone can shed some light on.

Occasionally when my laptop connects to my Billion 7800 modem router (801.11n), the connection is successful however the internet does not work? The only workaround that I found to work is to Disable the wireless or networking and then enable it again. Sometime this may need a few a go before the wireless and internet works again.

Below is the difference in the route table when the wireless/internet works and don't:

Wireless connects but no internet:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.109.0    *               255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
172.16.0.0      *               255.255.255.0   U     0      0        0 vmnet1
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
```

Wireless connects and internet works:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.109.0    *               255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
172.16.0.0      *               255.255.255.0   U     0      0        0 vmnet1
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         billion.matrix. 0.0.0.0         UG    0      0        0 wlan0
```

From the difference it appears when my default gateway is an IP address only then the laptop has problem routing the traffic?

Some additional information:

# My home WiFi has a hidden SSID
# Laptop doesn't have problem on other WiFi network, eg. at work and friend's house
# Wired networking works no problems

This problem isn't serious (just a bit annoying) so if someone can give me some pointers then that would be great!

Thanks =)

---

