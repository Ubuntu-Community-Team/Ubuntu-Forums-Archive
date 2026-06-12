---
title: "Installation of DNS and DHCP in UbuntuServer edition"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by vijaykalmani@yahoo.com on 2008-12-22
Hi Guys,
We have just migrated to Open Source Software Ubuntu 8 server edition for our servers in educational institute. We need help in installation of DNS server and DHCP server. 
Let i explain u the situtation. I need 

DNS name : mlbplinux.com
DHCP : server ip: 192.168.2.22
DHCP ip's from : 192.168.2.2 to 192.168.2.85
            192.168.2.105 to 192.168.2.225
            192.168.2.245 to 192.168.2.250

Rest of the ip's i need to reserve them.
I basic step by step or a GUI based help will be more appreciable.

---

### Post by andguent on 2008-12-22
I would recommend installing dnsmasq from apt-get (or aptitude). If you read EVERYTHING in the newly installed /etc/dnsmasq.conf, it should explain itself very well.

To get it started/testing, do a:
sudo /etc/init.d/dnsmasq restart

---

### Post by Iowan on 2008-12-22
Here's a [Dnsmasq]("https://help.ubuntu.com/community/Dnsmasq") help page. The [Perfect server]("http://www.howtoforge.com/perfect-server-ubuntu-8.10") article on howtoforge.com installed bind9 for DNS and didn't set up DHCP (although DHCP3 is common).

---

