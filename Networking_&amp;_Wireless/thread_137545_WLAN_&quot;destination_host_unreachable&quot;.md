---
title: "WLAN &quot;destination host unreachable&quot;"
date: 2006-02-28
forum: Networking &amp; Wireless
---

### Post by btb on 2006-02-28
I just installed kubuntu after not touching it for 2 years and run into a network configuration problem. I have an ASUS laptop with an Intel WLAN wireless pro network card. The card is detected without installing additional drivers.

I set up the /etc/network/interface file by hand because the kde configuration program didn't work.

```

iface eth1 inet static
   address 192.168.2.122
   netmask 255.255.255.0
   network 192.168.2.0
   broadcast 192.168.2.255
   wireless-mode managed
   wireless-essid Home
   wireless-key1 s:<zip>
   dns-nameservers 192.168.2.1
   wireless-key s:<zip>
   gateway 192.168.2.1
   wireless-channel 11

```
The iwconfig and ifconfig command informs me that everything is correct set up. The mac-address of the Acces Point in iwconfig is correct.

But for some reason I cannot ping anything else then de wlan card itself.

Using the ping command on the router results in a "desination host unreachable". This usually indicates that something is wrong with the route.

```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth1

```

But I can't see anything wrong with it. Does anyone has an idea?

<small addition>
The kwifimanager indicates that the laptop has a connection with the wlan.

---

### Post by claes on 2006-02-28
[QUOTE=btb]
```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0

```

But I can't see anything wrong with it. Does anyone has an idea?

<small addition>
The kwifimanager indicates that the laptop has a connection with the wlan.[/QUOTE]

This looks strange.
You can access the 192.168.2.0 network by going out on interface eth1.  But to access your default gateway that is on 192.168.2.0 network you go out on the eth0 interface. That's not correct. What config do you have on the eth0 device?

Claes

---

### Post by btb on 2006-02-28
My mistake, I had no internet on the laptop so instead of typing everything over I decided to copy paste it from my gentoo box and edit it. On that way the indenting remains. But I forgot something...

---

