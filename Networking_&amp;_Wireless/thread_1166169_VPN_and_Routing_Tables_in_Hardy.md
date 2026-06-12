---
title: "VPN and Routing Tables in Hardy"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by ToddFisher on 2009-05-21
I have read a lot of threads about VPN, but can't find an answer that I understand.  I am trying to connect to Witopia using OpenVPN, but when I connect I lose all access to the internet.  I cannot even ping a DNS.  When I disconnect, the internet connection returns.  I copied the config files over from windows and OpenVPN works fine in Windows.

I have asked for help from Witopia and they point me towards the routing tables not updating after connecting.  Has anyone else had this problem?  How do I reset the routing tables?

Thank you for any help.  

Todd


Before connecting VPN:

vale@hotrod:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan0

After connecting VPN:

vale@hotrod:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
38.100.141.140  192.168.1.1     255.255.255.255 UGH       0 0          0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 tun0

---

### Post by superprash2003 on 2009-05-21
try this [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

