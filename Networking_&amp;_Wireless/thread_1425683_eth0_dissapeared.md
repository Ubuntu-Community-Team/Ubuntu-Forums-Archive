---
title: "eth0 dissapeared"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by sinchan_ on 2010-03-09
hi

Ubuntu server 9.10. I have configured my network connection using GUI Network connection. It worked fine with DHCP, but when I assigned a fixed IP eth0 has dissapeared 

how can I restore it?

---

### Post by koszta on 2010-03-09
first of all make sure that it has not only disappeared from GUI (open a terminal and type ifconfig) if you see it there then it is a GUI problem. Otherwise (which is more probable) type lspci (if your card is in PCI bus) or lsusb (if you use USB card). Make sure that it is there. If so then rebooting should solve the problem. If not then you are missing a driver and you have a problem (although it can be solved of course :) ). 
In case you can see in lspci or lsusb and still dont see it after reboot follow [these intructions ]("http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames"). You are mostly only interested in those talking about udev naming devices

---

### Post by koszta on 2010-03-09
also see this [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/]("http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/")

It might help you some tho it is mostly for manual interface configuration

---

### Post by sinchan_ on 2010-03-09
finally solved launching system in rescue mode (I configured interfaces and resolv.conf before posting this thread)

Thanks 4 help, finally rescue mode helped

---

