---
title: "lookup ip address, subnet mask, gateway, and dns at same time"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by COKEDUDE on 2011-02-13
Is there a command that can lookup ip address, subnet mask, gateway, and dns all at the same. I know ifconfig can lookup ip address and subnet mask. I know route -n can lookup gateway. Not sure about a dns command. So I hope there is a way to lookup ip address, subnet mask, gateway, and dns all at the same.

---

### Post by COKEDUDE on 2011-06-08
Does anyone know a command to do this?

---

### Post by jwcalla on 2011-06-08
When you say "all at the same time", would you consider the following to be cheating?

```
ifconfig eth0 | grep "inet addr" ; route -n | grep UG ; grep nameserver /etc/resolv.conf
```

---

### Post by COKEDUDE on 2011-06-08
> **jwcalla said:**
> When you say "all at the same time", would you consider the following to be cheating?

```
ifconfig eth0 | grep "inet addr" ; route -n | grep UG ; grep nameserver /etc/resolv.conf
```

That's awesome. I can put it into a shellscript and execute it really easy and quickly :). I just didn't want to have to type out ifconfig, route -n, and grep /etc/resolv.conf every single time I need this info. My ISP is absolutely terrible so I need this info quite often. 

I modified this a little :). 
```
ifconfig | grep "inet addr" ; echo gateway; route -n | grep UG ; echo dns; grep nameserver /etc/resolv.conf

```


Someone made this on another forum. Your way is more compact so I think I like your way more. 

```
#! /bin/bash
ifconfig
echo
echo Gateway"               "Interface
route -n | awk '/UG/ {printf "%-21s %s\n",$2,$8}'
echo
echo DNS Servers
awk '/nameserver/ {print $2}' /etc/resolv.conf
echo
echo DHCP Server
awk '/dhcp-server-identifier/ {print $3}' /var/lib/dhcp3/dhclient.leases
```

---

### Post by jwcalla on 2011-06-08
If you're running gnome you can enable the NetworkManager Applet and then you can easily get this info by right clicking on the icon in the indicator panel.  (Ok this is 10.10, not sure how it is in 11.04.)  I think you know this already though and need the CLI for other reasons but I figured I'd mention it just in case or for any future forum searches.  :)

---

### Post by COKEDUDE on 2011-07-30
> **jwcalla said:**
> If you're running gnome you can enable the NetworkManager Applet and then you can easily get this info by right clicking on the icon in the indicator panel.  (Ok this is 10.10, not sure how it is in 11.04.)  I think you know this already though and need the CLI for other reasons but I figured I'd mention it just in case or for any future forum searches.  :)

Yep :). Its for a ubuntu server.

---

