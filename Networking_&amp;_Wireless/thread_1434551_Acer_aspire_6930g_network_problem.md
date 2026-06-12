---
title: "Acer aspire 6930g network problem"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by ravnen620 on 2010-03-20
Hey Ubuntu users.

I Just installed Ubuntu 9.10 and my network card ain't working.

It just says, when i clikc the icon, : VPN Connections. And that no device is found i think.

Please help me! I love ubuntu and its looks and cool things.

I have a Acer Aspire 6930g running win7 64bit.

My network cars is: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet controller.

/ thanks ;)

---

### Post by rory526 on 2010-03-20
what does 
```
sudo ifconfig -a
```
show you?

---

### Post by ravnen620 on 2010-03-21
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)
 
mail me: [EMAIL="l-alle-94@hotmail.com"]l-alle-94@hotmail.com[/EMAIL]

---

### Post by rory526 on 2010-03-21
"ifconfig -a" lists all the network interfaces. In the output you have posted, only the loop-back interface is present. Usually the wireless interface will be called "wlan0" or "eth1".

I think you need to see if there is a Linux driver for your wireless card. I think the Atheros AR8121/AR8113/AR8114 PCI-E Ethernet controller is for your wired connection, so to find out the make and model of your wifi card, please post the output of:

```
lspci
```

This command lists the hardware connected to the pci slots in your computer one of which should be your wireless card.

Then we search for lists of wifi cards supported by linux to see if there is a driver.
 
Don't worry, if there isn't a Linux driver for your card, in many cases, you can use a program called Ndiswrapper to create a form of your windows driver that is usable in Linux.

---

### Post by rory526 on 2010-03-21
Hi again,

the Acer aspire 6930g seems to use the Intel® WiFi Link 5100 wireless card. (Please check this with lspci.) Intel seem to supply a linux driver for this card which can be downloaded from the following site:

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&ProdId=3062&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=17045&ProdId=3062&lang=eng)

Hope this solves it!

---

