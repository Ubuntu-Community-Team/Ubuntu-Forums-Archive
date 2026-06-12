---
title: "How to give my VirtualBox OSE a static IP Address?"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by Habboblob on 2010-03-18
How can I give my VirtualBox OSE a static IP address.
My virtualbox is running Windows Xp 32-bit, and I am wanting to give it a static IP Address.

For example, my ubuntu pc has the ip address, 192.168.2.101
I want my VirtualBox to have the ip address, 192.168.2.201

I also want my Virtualbox to have port 95 open.

Thanks

---

### Post by Fire_Chief on 2010-03-18
The configuration of your NIC in Vbox should have options like NAT/Bridged/host only. If you choose the Bridged option, it will make your VBox machine talk directly on the LAN just like your Ubuntu PC. Then just set the IP manually in XP for the Local Area Connection.

Cheers!

---

