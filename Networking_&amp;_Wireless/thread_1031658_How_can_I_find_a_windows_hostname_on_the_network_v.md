---
title: "How can I find a windows hostname on the network via IP with Ubuntu?"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-01-05
Long story short... at work (school district) we have a full blown Windows network. (:() I however have a spare computer set up that runs Ubuntu so I can use various utilities on it.

We found a student who was instant messaging. *tisk tisk* and we have their IP. We ran ping -a on the IP but it didn't pull the host name as it should.

Using Ubuntu Intrepid, is there any way I can dig up the host name from the IP that I have?

---

### Post by capscrew on 2009-01-05
> We ran ping -a on the IP but it didn't pull the host name as it should.How does that work?

Quoting the ping man page:> ping -a     Audible ping.


Try this:```
arp -a <ip_address>
```

---

### Post by Copernicus1234 on 2009-01-05
Also try the host command:

```

host <ip>

```

---

### Post by Roasted on 2009-01-05
if you go to command prompt in windows and type

ping -a 10.0.0.1

It'll give you the host name of 10.0.0.1 + ping it 4 times as usual.

When I pinged -a myself, it gave me my host name.
When I pinged -a the IP in question, it didn't give me a host name... which is what I need.

---

### Post by Roasted on 2009-01-05
> **Copernicus1234 said:**
> Also try the host command:

```

host <ip>

```


Like this?

jason@jason-intrepid:~$ host 192.168.1.100
Host 100.1.168.192.in-addr.arpa. not found: 3(NXDOMAIN)
jason@jason-intrepid:~$ 



192.168.1.100 should be = "Curtdesktop"

---

