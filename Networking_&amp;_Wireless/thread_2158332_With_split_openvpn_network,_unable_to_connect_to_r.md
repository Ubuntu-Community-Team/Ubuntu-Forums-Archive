---
title: "With split openvpn network, unable to connect to remote server via vpn"
date: 2013-06-28
forum: Networking &amp; Wireless
---

### Post by CptanPanic on 2013-06-28
I am running ubuntu 12.04 and only want the vpn for specific applications that can bind to vpn port(address). If I connect to the VPN with all the traffice routed through the VPN port everything works fine. If I check option "Use this connection only for resources on its network", then other programs can reach the internet, but I cannot connect to a remote server binded to the vpn port, such as "telnet google.com 80 -b " It seems that I can get packets out, but maybe not in. Anyone know what is wrong?

With "Use this connection only for resources on its network" set: (Can't connect to remote server just using tun0 (10.187.1.9)

```
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth2
10.187.1.1      10.187.1.9      255.255.255.255 UGH   0      0        0 tun0
10.187.1.9      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
130.185.155.58  192.168.1.1     255.255.255.255 UGH   0      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth2
192.168.100.0   0.0.0.0         255.255.255.0   U     0      0        0 eth2

```
Default Option: (I can connect to remote server using tun0, but all traffic is being routed through tun0)

```
0.0.0.0         10.187.1.9      0.0.0.0         UG    0      0        0 tun0
10.187.1.1      10.187.1.9      255.255.255.255 UGH   0      0        0 tun0
10.187.1.9      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2
185.3.135.58    192.168.1.1     255.255.255.255 UGH   0      0        0 eth2
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth2
192.168.100.0   0.0.0.0         255.255.255.0   U     0      0        0 eth2
```

---

