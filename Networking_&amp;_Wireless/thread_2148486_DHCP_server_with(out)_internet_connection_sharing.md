---
title: "DHCP server with(out) internet connection sharing"
date: 2013-05-25
forum: Networking &amp; Wireless
---

### Post by paweltbg94 on 2013-05-25
Hello. I'm using the Ubuntu Server 12.04.2 LTS on the computer with 2 ethernet interfaces and I want to set up a DHCP server on it with shared internet connection. I had no problems with DHCP server, the IP addresses and other network informations are assigned correctly according to the dhcpd.conf file. The problem is that the internet connection for my DHCP clients does not work (for the server itself only the DNS lookup works, but it probably uses the "LAN" ethernet device instead of "WAN"). I have followed this guide:

[Chapter 4 -Ubuntu Internet Gateway Method (iptables)]("https://help.ubuntu.com/community/Internet/ConnectionSharing#Ubuntu_Internet_Gateway_Method_.28iptables.29")

The only thing I have changed is network range to 192.168.0.0/16 and I used /etc/network/interfaces file to configure network interfaces instead of "ip" command.
Now any DHCP client can only ping to the DHCP server and nothing else, the route ends here :(. 

Various configs and commands outputs are attached.

---

### Post by paweltbg94 on 2013-05-25
Rest of attachements + lspci:

[https://www.dropbox.com/s/w4mngpjgobwasf4/lspcivv.txt](https://www.dropbox.com/s/w4mngpjgobwasf4/lspcivv.txt)

---

