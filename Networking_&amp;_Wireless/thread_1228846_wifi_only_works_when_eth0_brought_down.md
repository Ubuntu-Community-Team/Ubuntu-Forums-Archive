---
title: "wifi only works when eth0 brought down"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by izziere on 2009-08-01
I can only get my wireless network adapter up and running by bringing down eth0:

```
sudo ifdown eth0
```

without that all pings to my router get lost.

This is the output from my /etc/network/interfaces file:

```

auto lo eth0
iface lo inet loopback

iface eth0 inet static
address 192.168.1.122
netmask 255.255.255.0
gateway 192.168.1.1


iface ath0 inet static
address 192.168.1.122
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid xxxxx

auto ath0
```

I am using an Atheros card and madwifi.

Thanks

---

### Post by Iowan on 2009-08-01
I've seen some threads on bridging (haven't tried it - so I still don't understand it), but to me, it still seems like a bad idea to have two interfaces with the same IP address.  Try changing one  or the other and see if it works after restarting networking.

---

### Post by slakkie on 2009-08-01
> **Iowan said:**
> I've seen some threads on bridging (haven't tried it - so I still don't understand it), but to me, it still seems like a bad idea to have two interfaces with the same IP address.  Try changing one  or the other and see if it works after restarting networking.

Then you will have problems too, which IP to route over which interface, so he needs to change both IP adress and metrics. If he prefers wifi he should give his LAN a higher metric. Else, the otherway around.

---

### Post by izziere on 2009-08-02
Great - that solved it.  My confusion arose because this config worked in the past and I wonder whether one of the updates made it become a bit more sensitive to such things.

Ideally I want one IP address and for the system to try eth0 and, if not connected, try ath0.  Is there any way of doing this, or shall I just stick to having two IP addresses for the one machine?

Thanks again

---

### Post by Brandon Williams on 2009-08-02
You could use a pre-up method for the wireless interface that makes ifup skip the wifi interface if eth0 is active. Look at the files in /usr/share/doc/ifupdown/examples to start getting ideas about how this could be done.

---

### Post by izziere on 2009-08-07
Actually, no it doesn't solve it.  Grr.  Here is interfaces:

```
auto lo eth0
iface lo inet loopback

iface eth0 inet static
address 192.168.1.123
netmask 255.255.255.0
gateway 192.168.1.1

iface ath0 inet static
address 192.168.1.122
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid xxxxx
```

It also means I have to manually mount a server drive every time I log on or every time I restart networking.

---

