---
title: "Can I setup DNS using cli..."
date: 2006-03-22
forum: Networking &amp; Wireless
---

### Post by ssalman on 2006-03-22
I'm trying to setup DNS using cli...

I have a static IP home network setup, when I use "ifconfig ath0 192.168.2.4" I get a connection to my router and I can test it through "ping 192.168.2.1", but I can't "ping www.google.com" :( using the below command doesn't help either ```
echo "nameserver 192.168.2.1" > /etc/resolv.conf
``` 
if I use dhcp throught "sudo dhclient ath0" I get a perfect connection and can "ping www.google.com" with no problems.

what is the correct way to setup DNS through cli ??? 

thanks.

---

### Post by yota on 2006-03-23
Maybe your is not a DNS problem... it could be a routing problem.

If you can't ping even 66.249.87.99 (which is google's ip) when you have a static configuration look at the output of
```

sudo route

```
If there's not a "default" line you're missing the default gateway, or it's not the correct one.
Compare the output before and after dhclient to spot if this is the problem.
You can manually add a gateway with:
```

sudo route add default gw x.x.x.x eht0

```
And by adding a "gateway x.x.x.x" line in /etc/network/interfaces

Finally if you want to test if DNS is working (and nothing more) you can also use "nslookup www.google.com" instead of "ping www.google.com"; the first only resolve the name, the second also tryes to actually contact the server.

Hope this helps.

---

### Post by ssalman on 2006-03-26
Thanks Yota, you hit the problem right on the head :) it was the gateway and it was fixed exactly like you described... I have been running in circles and posting in multiple threads, only to find I was asking the wrong question.... THANKS!!!

---

### Post by ssalman on 2006-03-26
DELETED: Duplicated post

---

