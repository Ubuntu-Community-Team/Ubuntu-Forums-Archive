---
title: "Connection Established but no internet Ubuntu 9.10"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by svkndv on 2009-11-12
Unable to setup WLAN on machine withLinksys WUSB54GC V3 adapter. I get connection established message but can't browse internet.

ifconfig -a output for wlan0

wlan0     Link encap:Ethernet  HWaddr 00:23:69:d9:ad:52  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:17760 (17.7 KB)


iwconfig output

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Asok"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 1E:A2:05:A5:6E:28   
          Tx-Power=8 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by t0mppa on 2009-11-12
Ok, can you post the results of the following commands from terminal:```
ip route list
ping <gateway_ip>
ping 74.125.79.99
ping www.google.com
```

You can see the gateway IP in the *ip route list* output, here's an example:```
$ ip route list
192.168.0.0/24 dev wlan0  proto kernel  scope link  src 192.168.0.100  metric 2 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
default via [COLOR="Red"]192.168.0.254[/COLOR] dev wlan0  proto static
```

And yes, it's the red one. If you don't see a default route at all, then you can forget about the pings, since no traffic is getting routed outside your local network.

---

### Post by svkndv on 2009-11-16
> **t0mppa said:**
> Ok, can you post the results of the following commands from terminal:```
ip route list
ping <gateway_ip>
ping 74.125.79.99
ping www.google.com
```

You can see the gateway IP in the *ip route list* output, here's an example:```
$ ip route list
192.168.0.0/24 dev wlan0  proto kernel  scope link  src 192.168.0.100  metric 2 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
default via [COLOR="Red"]192.168.0.254[/COLOR] dev wlan0  proto static
```

And yes, it's the red one. If you don't see a default route at all, then you can forget about the pings, since no traffic is getting routed outside your local network.

Got solution from another [thread]("http://ubuntuforums.org/showthread.php?t=1155941&page=16"), linksys adapter used a different driver by default.

---

### Post by Iowan on 2009-11-16
[SOLVED]?
(Thread Tools)

---

