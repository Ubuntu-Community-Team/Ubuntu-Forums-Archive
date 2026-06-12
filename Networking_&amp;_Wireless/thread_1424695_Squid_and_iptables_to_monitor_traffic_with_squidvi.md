---
title: "Squid and iptables to monitor traffic with squidview"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by gvigner on 2010-03-08
Hi,

My goal is only to monitor the traffic on my machine using **squidview**.

So, I have installed **squid** on my machine with the following parameters in **/etc/squid/squid.conf** :

```
acl internal_network src 192.168.1.0/24
http_access allow internal_network
```

When I configure the proxy in my browser on **localhost:3128**, I can see logs scrolling in **squidview**. I'd like now to get the same result, but using **iptables**, and not by having to set the proxy in my browser.

I have tested three different iptables, but unsuccessfully :

```
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128
iptables -t nat -A PREROUTING -i eth0 -s 192.168.1.0/24 -p tcp --dport 80 -j REDIRECT --to-port 3128
iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to 192.168.1.101:3128
```

But none of them worked for me.

Can someone help me to make it work ?

Thanks,
Gil

---

### Post by r939ick on 2010-03-09
Those rules will work for a second machine trying to use your host as a gateway, but the problem with requests originating from localhost is that they don't match "-i eth0".  In fact, locally generated packets don't traverse PREROUTING at all.

Try something like:

```

# iptables -t nat -F
# iptables -t nat -A OUTPUT -o eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128
```

---

