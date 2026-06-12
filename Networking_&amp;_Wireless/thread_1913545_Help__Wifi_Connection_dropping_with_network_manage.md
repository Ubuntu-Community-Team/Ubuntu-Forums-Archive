---
title: "Help : Wifi Connection dropping with network manager"
date: 2012-01-22
forum: Networking &amp; Wireless
---

### Post by speigel205 on 2012-01-22
Hi

I am using ubuntu 11.10. The driver for my wireless card is the Ralink rt5370STA. In Network Manager I can connect fine but the connection is dropped each time approximately between some seconds to a few minutes. I should reconnect again to make it work.
The strange also is that when connection is dropped, iwconfig and ifconfig continue to show me associated with my access point and the ip of association in ifconfig as well.

I am using network manager with all default options, I always still near my access point and not far from it, it is frustrating to get connection dropping each time like that so I which if someone can assists me.

A@

---

### Post by aryabhatt on 2012-04-18
I don't know if it is too late. Just to go on record for others having same problem. Install wicd. You don't need to remove network-manger. They can live together. When you are experiencing problems, just stop network-manager and start wicd.

Install wicd:
```
sudo apt-get install wicd
```

when having problems:
```
sudo service network-manager stop
```

run wicd-clinet from terminal.
```
wicd-client
```

---

