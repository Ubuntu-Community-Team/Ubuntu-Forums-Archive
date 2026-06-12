---
title: "nmap ping a pc with icmp disabled"
date: 2010-11-13
forum: Networking &amp; Wireless
---

### Post by Sycron on 2010-11-13
I tried to ping some of the pcs on the local network but for those with icmp disabled it doesn't work. Any ideas?
I've used```
nmap -sP 192.168.2.0/24
```

---

### Post by patch11 on 2010-11-13
Hi,

did you tried

```

nmap -PS 192.168.2.0/24

```

This will send TCP-Syn's to the machines and check if a RST or SYN/ACK came back.

---

### Post by Sycron on 2010-11-15
All hosts from 0 to 255 appear to be up that way. I have no idea if it counts but pc's are connected to a switch.

---

### Post by patch11 on 2010-11-15
Are you trying to do the nmap to hosts that are behind a firewall/nat?

The firewall/nat might send out the TCP-RST's.

---

