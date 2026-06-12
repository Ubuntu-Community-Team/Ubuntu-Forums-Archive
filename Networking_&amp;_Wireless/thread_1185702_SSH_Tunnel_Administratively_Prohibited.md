---
title: "SSH Tunnel Administratively Prohibited"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by newsboy on 2009-06-12
I am trying to create an SSH VPN. I have attempted to follow the directions [https://help.ubuntu.com/community/SSH_VPN]("https://help.ubuntu.com/community/SSH_VPN"). 
When I attempt to connect from my Macbook to Ubuntu I receive the waring 
```
debug1: Remote: Server has rejected tunnel device forwarding
channel 0: open failed: administratively prohibited: open failed
```
I believe have fix this by issuing the comand
```
echo 1 | sudo tee /proc/sys/net/ipv4/ip_forward
echo 1 | sudo tee /proc/sys/net/ipv4/ip_nonlocal_bind
```

I am then able to connect. when I execute ifconfig on the mac i see the device tun0. However, on the ubuntu box I do not see tun0. This has been replicated on my desktop that I run ubuntu on as well as a VM with a clean install.

*** I was able to get this working. When i type in the command ifconfig tun0 on the ubuntu box is shows tun0. But when I just type ifconfig it doesn't show it.

---

