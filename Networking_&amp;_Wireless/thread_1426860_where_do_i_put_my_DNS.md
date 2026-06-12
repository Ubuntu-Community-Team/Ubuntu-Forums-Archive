---
title: "where do i put my DNS?"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by colifato13 on 2010-03-10
I had ubuntu for about 2 days now and i want to configure my network settings, but i cant find a place to put my DNS can someone help me.

---

### Post by dineshs on 2010-03-10
```
sudo gedit /etc/resolv.conf
```
and add your DNS as ```
nameserver x.x.x.x
```

---

### Post by colifato13 on 2010-03-10
thanks, where do i write it? terminal?

---

### Post by dineshs on 2010-03-10
Yes(Applications-accessories-terminal).But before that can you post what is already in that file
```
cat /etc/resolv.conf
```

---

### Post by Iowan on 2010-03-10
DHCP address or static? (both of which can be configured via Network Manager) Network Manager tends to overwrite that file - but nameservers can be added via NM, too.

BTW, use **gksudo** with **gedit**
[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

