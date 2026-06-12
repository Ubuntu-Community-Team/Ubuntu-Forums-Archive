---
title: "ubuntu 10.04 .I turned off the cow &quot;Network Manager&quot;  SIOCADDRT: process is dos'n ex"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by wertum on 2010-08-03
ubuntu 10.04

1.I  turned off the cow "Network Manager"
2. I'm enter to terminal :
route add default gw 192.168.1.50
OOPS!! Terminal give me a Eroor:
[SIZE=2][COLOR=#000099]SIOCADDRT: process is dos'n exists

[/COLOR][/SIZE]Please, help me.

---

### Post by viralmeme on 2010-08-03
> **wertum said:**
> IOCADDRT: process is dos'n exists

[Solution to SIOCADDRT no such process on Ubuntu]("http://www.digitalsanctum.com/2009/03/22/solution-to-siocaddrt-no-such-process-on-ubuntu/")

---

### Post by Hetepeperfan on 2010-08-03
Hi you should run these processes as Super User.

Thus type:

```
sudo route add default gw 192.168.1.50
```

best Maarten

---

### Post by wertum on 2010-08-03
Problem is not fixed.

:-(

any ideas?

---

### Post by Hetepeperfan on 2010-08-03
Do you know the ip-address of you router? 192.168.1.50 sounds more like your own ip addres More likely adresses are 192.168.1.1 or 192.168.0.1 You can google for your router to see what it's default address is.

Hope this helps,

Kind regards, Maarten

---

