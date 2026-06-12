---
title: "can't log on to router"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by v923z on 2010-03-05
Hi All,

I have a WRT54G router, and I would like to log on to it, but for some reason, I can't. I can ping the router, and and when I try ssh into it, ssh returns with 
```
ssh: connect to host 192.168.1.125 port 22: Connection refused
```which seems to imply that 192.168.1.125 is a valid address, for 192.168.1.1 returns
```
ssh: connect to host 192.168.1.1 port 22: no route to host
```But I just can't log on to the router, neither via ssh, not via web. Has anyone got any idea as to what can be wrong?
Thanks,
v923z

---

### Post by Iowan on 2010-03-05
Worst case, there's the "reset" button...
Seems like odd address for router, but it's not cast in stone - so you could use what you want (within limits).  Pings work for 192.168.1.125 but not 192.168.1.1?

---

### Post by DGortze380 on 2010-03-05
> **v923z said:**
> Hi All,

I have a WRT54G router, and I would like to log on to it, but for some reason, I can't. I can ping the router, and and when I try ssh into it, ssh returns with 
```
ssh: connect to host 192.168.1.125 port 22: Connection refused
```which seems to imply that 192.168.1.125 is a valid address, for 192.168.1.1 returns
```
ssh: connect to host 192.168.1.1 port 22: no route to host
```But I just can't log on to the router, neither via ssh, not via web. Has anyone got any idea as to what can be wrong?
Thanks,
v923z

Whats the address and netmask of the host?

---

### Post by r939ick on 2010-03-05
Is this running the standard firmware, or something like dd-wrt/tomato/OpenWRT?  With the stock linksys firmware, you cannot ssh in.

In either case, you won't be able to access the web interface over the wireless network (for hopefully obvious security reasons).  You'll need to connect to it over wired ethernet.

---

### Post by pastalavista on 2010-03-05
Use a browser. Enter 192.168.1.1 in the address bar (I have the same router) Default login -user (blank)-password 'admin'

---

### Post by v923z on 2010-03-06
> **r939ick said:**
> Is this running the standard firmware, or something like dd-wrt/tomato/OpenWRT?  With the stock linksys firmware, you cannot ssh in.

In either case, you won't be able to access the web interface over the wireless network (for hopefully obvious security reasons).  You'll need to connect to it over wired ethernet.

It has kamikaze installed on it. I have managed to log on to it, thanks to all for the replies. I think, the problem was that on the computer, I set 192.168.1.125 for the IP address, while the router had 192.168.1.1. After I re-set the address on the computer, it worked all right. However, it still baffles me why I could ping 192.168.1.125, if the router address was 192.168.1.1. Most weird.
Thanks again,
v923z

---

### Post by r939ick on 2010-03-06
> **v923z said:**
>  on the computer, I set 192.168.1.125 for the IP address
> However, it still baffles me why I could ping 192.168.1.125Perhaps you were pinging the computer instead of the router?

---

