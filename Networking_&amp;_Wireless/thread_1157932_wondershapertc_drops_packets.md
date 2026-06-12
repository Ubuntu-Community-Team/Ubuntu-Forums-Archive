---
title: "wondershaper/tc drops packets"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by ilovemistakes on 2009-05-13
I have ubuntu 9.04 server with openvpn server installed. eth0 is connected to the internet, tun0 is connected to OpenVPN client. eth0 is 10Mbit/s, tun0 is about 2mbit/s. I want to limit speed for OpenVPN clients to, say, 1mbit/s. I used wondershaper to do the trick.
```
sudo wondershaper tun0 256 256
```
Speedtest on client says that it have 0.1mbit/s up/down. Downloading of big files starts at big speed and slows down to ~15kb/s. But if I increase limit to
```
sudo wondershaper tun0 1024 1024
```
downloading stops after a few megabytes. I tried to add tc tbf disciplines manually and got the same problem.
When downloading stops,
```
netstat -nat | grep 1194
```
shows me that Send and Recv queues are growing.
What am I doing wrong?

---

