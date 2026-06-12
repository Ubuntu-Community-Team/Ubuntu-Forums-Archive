---
title: "VPN Connection to Windows Network"
date: 2012-10-24
forum: Networking &amp; Wireless
---

### Post by thebeest on 2012-10-24
Hi there

I am trying to connect my fresh xubuntu 12.10 installation to a windows network but the connection only seems to work for 10-20 seconds and then it is unusable. By this I mean that I can connect to http, ssh, rdp for those first few seconds then the connections all time out. Network manager keeps the VPN connection active for a another few minutes then it disconnects.

I have tested the connection with the same gateway/credentials on a Windows 7 machine and it worked first time, thus ruling out problems on the server side.

I have tried following format c's guide in [http://ubuntuforums.org/showpost.php?p=10212363&postcount=3](http://ubuntuforums.org/showpost.php?p=10212363&postcount=3) but the connection is just not workable.

At first my routing table looked like this:

```
Kernel IP routing table
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
81.2.x.x        192.168.0.1     255.255.255.255 UGH   0      0        0 wlan0
81.2.x.x        192.168.0.1     255.255.255.255 UGH   0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.0.1     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0

```

I had to add 192.168.0.0 | 255.255.255 | 81.2.x.x into the routes configuration for the VPN connection so I could connect to devices on the network other than 192.168.0.1. After these additions the routing table looks like this:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
81.2.x.x        192.168.0.1     255.255.255.255 UGH   0      0        0 wlan0
81.2.x.x        0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
81.2.x.x        192.168.0.1     255.255.255.255 UGH   0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ppp0
192.168.0.0     81.2.119.34     255.255.255.0   UG    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.0.1     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0

```

Any ideas why I can only use the connection for <20 seconds before it gives up?
Any help would be greatly appreciated!

---

### Post by thebeest on 2012-10-24
It might be worth noting that I tried the connection on an old install of Ubuntu 12.04. But I wasn't a fan of Unity and Gnome3 was getting annoying so I did a fresh install of xubuntu with compiz and emerald and it much resembles the desktop I knew and loved from 9.10. Everything has worked so far without any twiddling but I just can't get the VPN to work.

Please let me know if anyone knows how to resolve this!

---

### Post by thebeest on 2012-11-25
Can anyone help me out on this one? I just tried the VPN connection again offsite with a different ISP and I get the same problem. I can SSH, HTTP, HTTPS etc for about 20 seconds and then nothing.

---

### Post by ahallubuntu on 2012-11-25
What kind of VPN is it?  Does your VPN server have a logfile that might help you debug what's going wrong?

---

