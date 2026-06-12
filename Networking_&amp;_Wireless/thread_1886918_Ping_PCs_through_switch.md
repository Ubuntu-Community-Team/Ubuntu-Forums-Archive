---
title: "Ping PCs through switch"
date: 2011-11-25
forum: Networking &amp; Wireless
---

### Post by Roque on 2011-11-25
My net setup is as follows:
```
internet-----modem----switch----PC1
                         |
                         |
                         -------PC2

```   

I'd like to ping PC2 from PC1 and vice versa 

Is this even possible? Sorry for the question but I am pretty new to this stuff

---

### Post by Doug S on 2011-11-25
Yes, you should be able to ping either way between PC1 and PC2.
I don't know if you would be able to do it by name though, maybe only by IP address.
Is what you show as "modem", just a modem and not a modem/router? If it is just a modem, then I assume your ISP is giving you 2 WAN IP addresses, one for each PC.

---

### Post by Roque on 2011-11-25
Thanks Doug

Yes, it is a modem-router. So let's say PC1 is eth0 (192.168.0.1) and PC2 is eth0 (192.168.0.2) as reported by: 
```
ifconfig -a
``` in every computer
And someone at PC1 writes: 
```
ping 192.168.0.2 
```
it should ping PC2 without problems?

Cos that does not work :(

---

### Post by Doug S on 2011-11-25
Check your iptables on both PC's and see if ICMP echo requests are being blocked.
I would use a terminal window and the command:
```
sudo iptables -v -x -n -L
```

---

### Post by Roque on 2011-11-25
Many thanks Doug!!

Indeed it was a firewall rule... now it works perfectly

See ya and many thanks again! :D

---

