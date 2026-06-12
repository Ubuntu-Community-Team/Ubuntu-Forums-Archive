---
title: "How to change DNS when you connect through VPN with Cisco Anyconnect"
date: 2011-08-05
forum: Networking &amp; Wireless
---

### Post by Codrin on 2011-08-05
HY, 
I am using Ubuntu 11, 32 bit. I connect to the internet using a wired connection with Cisco Anyconnect VPN Client 2.4. Using [Namebench]("http://code.google.com/p/namebench/") i can find which are the best DNS's for me.
The problem is as folows:
- Cisco Anyconnect VPN is overrinding the changes i make in "sudo gedit /etc/resolv.conf", meaning no matter what servers i put there, when i reconnect it will rewrite the file with the ISP's DNS;
- i added in "sudo /etc/dhcp3/dhclient.conf" the line "prepend nameservers x.x.x.x, y.y.y.y;" but the DNS adress remains the same; 

So, is there anyway i could go around this?
PS. Nothing else is working(openvpv, vpnc) to connect to the network unless the Cisco program.

---

### Post by Codrin on 2011-08-05
I also tried, while disconnected  from VPN, to left click my wired connection, then edit, then under the tab IPV4 settings, to add DNS server there.. still doesnt do it.. on the wired connection they become listed but when i connect the vpn and check, the ISP's is on

---

