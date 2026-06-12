---
title: "Frustrating network problems"
date: 2006-02-19
forum: Networking &amp; Wireless
---

### Post by caspar_wrede on 2006-02-19
I decided to give my little brother a chance at freedom and installed ubuntu on his desktop. Sadly I was a bit rattled by the number of problems that have arisen. The biggest is a network problem:

DHCP does not work. It works on the same machine when using knoppix. The output of lspci under knoppix and ubuntu seems indentical: 
```

Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller

```

When booted into ubuntu I can ping myself but not the gateway. During pinging the lights on the network card flash.

What can I do???

---

### Post by darth_vector on 2006-02-19
can you post the contents of /etc/network/interfaces please?

there should be a pair of lines that reads something like```
auto eth0
iface eth0 inet dhcp
```if there aren't, you should add them. you will have to do this as superuser```
sudo gedit /etc/network/interfaces
```

---

