---
title: "How do I check what my network and gateaway IP's are please?"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by amylase on 2009-10-24
Hi

I'm trying to setup [ISPConfig]("http://www.ispconfig.org/index.htm"). Part of the installation process requires I set up my network values in a particular file called "/etc/network/interfaces": 

iface eth0 inet static
address xx.xx.xx.xx
netmask xx.xx.xx.xx
network ?
broadcast xx.xx.xx.xx
gateway ?


I'm okay with xx.xx.xx.xx which are told by ifconfig (listed next to "inet addr", "Mask", and "Bcast" right?).

How do I check what my network and gateaway IP's are please?

I can see inet6 addr and HWaddr but they don't look like IP's. They have :: rather than .


Thanks very much.

---

### Post by r4lly on 2009-10-24
you can type 

$ ifconfig

and if u still confused  , just add --help in that command


:)

---

### Post by JBAlaska on 2009-10-24
Your Gateway Ip, is also the address you use to log into your router, generally 192.168.X.X (192.168.1.1 for linksys,d-link and many others) As r4lly said "ifconfig -a" will show it all to you.

---

### Post by tzicatl on 2009-10-24
> **amylase said:**
> Hi

How do I check what my network and gateaway IP's are please?



```
route -n
```

Also, if you're running GNOME you can right-click on the nm-applet icon and select "Information" (I don't recall the exact name on english"). A window opens with all the info you need.

Hope it helps. 

Regards

---

### Post by Iowan on 2009-10-24
Network and broadcast addresses may not actually be necessary. Typically, for a netmask of 255.255.255.0, the broadcast address is like the address, but ending in .255 (eg. 192.168.1.255). The network is the same number - ending in .0 (192.168.1.0), and the gateway ends in .1 (192.168.1.1 - as mentioned)... although I've seen other gateway's used - .254 in particular.

---

