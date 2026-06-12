---
title: "How to stop wvdial from overwriting /etc/resolv.conf?"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by frankvw on 2010-03-03
I use wvdial and a 3G modem to connect to the network. On the same host I also run bind9 which is authorative for my local network.

The problem is that when wvdial connects, it overwrites /etc/resolv.conf, which means that DNS lookups on that host no longer get made to localhost (as specified by the original resolv.conf file) and end up at the local instance of bind which is authorative for in-house hostnames, but end up with the ISP who doesn't know my in-house host names.

The local DNS forwards to the ISP, so the ISP's DNS'es are not required in resolv.conf.

How can I prevent wvdial from overwriting /etc/resolv.conf? Removing write privileges from /etc/resolv.conf did not work.

All response appreciated!!

// Frank

---

### Post by viralmeme on 2010-03-03
> **frankvw said:**
>  .. The problem is that when wvdial connects, it overwrites /etc/resolv.conf ..
I do believe resolv.conf gets overwritten with the settings in /etc/dhcp3/dhclient.conf
Uncomment out the prepend line and put your dns settings there and restart the network ..

/etc/dhcp3/dhclient.conf
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;

$sudo /etc/init.d/networking restart

---

### Post by GeorgeVita on 2010-03-03
Hi **frankvw**, if above did not solve it, try:
```
gksudo gedit /etc/ppp/peers/wvdial
``` REMOVE parameter **usepeerdns** and save file.
```
gksudo gedit /etc/wvdial.conf
``` add the following parameters (found after reading **man wvdial.conf**): ```
check DNS = no
auto DNS = no

```
More info: man pppd

Regards,
George

---

### Post by frankvw on 2010-03-03
Aha. I had tried editing wvdial.conf, and I had tried editing /etc/ppp/peers/wvdial, but I had not tried editing them both at the same time. :-)

Problem solved. Thank you for pointing me in the right direction!

// Frank

---

