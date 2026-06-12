---
title: "Network IPv4 settings"
date: 2013-08-08
forum: Networking &amp; Wireless
---

### Post by mtiwariin on 2013-08-08
Hi I am new to Ubuntu 13.04. There are two networks 

1. Using USB modem to connect to internet (IPv4 setting : Automatic (PPP) and default PPP settings)
2. Ethernet card to connect to another laptop machine. Ubuntu machine and laptop are connected using crossover ethernet cable. IPv4 settings are Method: Manual Static IP address 192.168.1.102 Subnet mask 255.255.255.0 and Gateway 0.0.0.0 DNS servers 192.168.1.1 , 8.8.8.8
Laptop IP address is 192.168.1.1

The issue:
The moment I specify gateway IP address other than 0.0.0.0 my internet connection stops working.

Can someone please help me understand why is this happening?

---

### Post by SeijiSensei on 2013-08-08
1)  You need to enable packet forwarding on the gateway box.  See /etc/sysctl.conf which explains this.

2)  You need to enable masquerading on the gateway box.  Read [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing).

---

### Post by daniel13 on 2013-08-08
Hey SeijiSensei, nothing is working for me either and I really need this internet connection! 

I have a laptop running W8 and a desktop dual booting vista/ubuntu. The vista boot connects fine, ubuntu will not. I have tried everything and just cannot get it to hook. 

Would really appreciate some assistance!

---

