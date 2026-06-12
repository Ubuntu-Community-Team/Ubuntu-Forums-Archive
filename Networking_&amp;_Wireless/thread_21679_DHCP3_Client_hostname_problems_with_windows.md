---
title: "DHCP3 Client hostname problems with windows"
date: 2005-03-23
forum: Networking &amp; Wireless
---

### Post by void on 2005-03-23
my laptop is in use at home, at work and other places.

in the company were using a windows server 2003 (Small Business Server 2003 to be axact), as DHCP and DNS Server.

everytime my laptop is requesting an ip it gets one, so no problem there.
but the server is not using my hostname.

problem 1: my pc is only reachable via my ip, and not via the hostname
problem 2: my pc is getting ips throughthe whole leases
day 1: ip 192.168.x.1
day 2: ip 192.168.x.23
day 3: ip anything in the lease

on the reverse lookup zone of the dns server the hostnames of these ips are listet as in use by other pcs of the company

other-pc-1 has the ip 192.168.x.1, when im using that ip

so someone who want to access the other-pc by hostname is reaching either me or the other pc cause the hostname has now two ips

in the forward lookup zone my ip is not listet

but in the dhcp server my ip is listet with my full qualified domain name

so im not reachable via my hostname

any suggestions ?

EDIT: i've forgotten following:
i have already searched the board, and changed the /etc/network/interfaces file and the /etc/dhcp/dhclient.conf file and added the hostnames

---

### Post by m68 on 2005-03-29
Hi,

I did this :

 **apt-get install dhcpcd**

---

