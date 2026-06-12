---
title: "Redirecting an IP address to another IP address and port"
date: 2010-12-17
forum: Networking &amp; Wireless
---

### Post by YPwn on 2010-12-17
I'm running Ubuntu 10.10 and I need to redirect IP address to another on an outgoing connection from my machine. For example, I open a web browser and go to:
10.0.0.1:1625

It redirects me to 192.168.1.1:921 but I still see 10.0.0.1:1625 in the address bar. I can't achieve this by editing /etc/hosts. I would be very thankful if you help me.

Thanks in advance!

---

### Post by Mosabama on 2010-12-17
This cant be achieved by /etc/hosts file.

you may want to use iptables specially if you want port forwarding as I understood from your example, its available in ubuntu.
```

iptables -t nat -A OUTPUT -j REDIRECT -p tcp -d 10.0.0.1/24 --dport 1625 --to-ports 921

```
if you want to remove this again:
```

sudo iptables -t nat -F

```

---

### Post by YPwn on 2010-12-18
Thanks, but I also need to redirect the IP to another IP like "hosts" does.

---

### Post by gmargo on 2010-12-18
Sounds like you want a simple proxy tool.  Take a look at **tinyproxy**.

---

### Post by Mosabama on 2010-12-18
> **YPwn said:**
> Thanks, but I also need to redirect the IP to another IP like "hosts" does.

You can always change the ip in the example to any ip you want in the network.

---

### Post by YPwn on 2010-12-20
Thanks, your help is appreciated. ;)

---

