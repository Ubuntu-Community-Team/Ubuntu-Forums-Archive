---
title: "network manager not working"
date: 2011-11-28
forum: Networking &amp; Wireless
---

### Post by alieblice on 2011-11-28
Hi

Ubuntu 11.10
vaio f13
my network manager is not working but it's recognizing  the hardware
 
when i click on the icon it writes :

```
wire network
device not managed

wirless networks
device not managed

```before this happens wireless was working but after using command 
```
iwconfig 
```wireless stop working too:confused: 


if any more data needed please tell me

---

### Post by zeljkojagust on 2011-11-28
Please check your /etc/network/interfaces file. Only a definition for loopback adapter should be present there for Network Manager to work.

---

### Post by praseodym on 2011-11-28
Hi,

please show

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
rfkill list
sudo iwlist scan
cat /etc/network/interfaces
```

---

### Post by alieblice on 2011-11-29
thanks guys  :)
network manager works perfectly now :)
i think the problem was with 
```
 /etc/network/interfaces
```file

but  i cant connect to ADSl and vpn doesn't work right 
it tells me that i connect to vpn but actually i lost my adsl  connection .  can this happen because i connect to adsl by pppoeconf command?  

i had these problems on 11.04 too
i check it with ubutnu 10.04 live cd . adsl was working wright .

---

