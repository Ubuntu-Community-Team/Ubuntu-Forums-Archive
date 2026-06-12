---
title: "DNS not working for local network"
date: 2006-01-24
forum: Networking &amp; Wireless
---

### Post by neko on 2006-01-24
Hi,

I am having problems getting DNS for work on my local (home) network.

Here is my setup:

DSL modem (10.0.0.138 ), connected to WRT54G wireless router (192.168.1.1)
One computer is wired up to the WRT54G.
A second computer is connected wirelessly to the WRT54G.
Both computers are running ubuntu 5.10

Both the DSL modem and WRT54G are running DHCP servers.
The DSL modem is running a DNS server, its Domain Name is set to "local.net".
The WRT54G has 10.0.0.138 set as a "static DNS".

Both computers receive 192.168.1.x IP addresses.  I can ping each computer, the WRT54G and DSL modem from each computer using IP addresses.
I can access the internet fine from both computers.

But I cannot ping either host from the other.

/etc/resolv.conf contains:

search local.net
nameserver 10.0.0.138
nameserver 192.168.1.1


Some questions:

1. Why does this not work? :) 

2. Is it OK to have both the DSL modem and router running DHCP servers?

3. Each hostname has a simple hostname (/etc/hostname):  "foo" and "bar".  Should these be "foo.local.net" and "bar.local.net"?

4. Even if I have "foo.local.net" in /etc/hostname, running "hostname" gives my "foo.local.net", but "hostname -d" results in "hostname: Unknown host".


Please help!

thanks,
neko

---

