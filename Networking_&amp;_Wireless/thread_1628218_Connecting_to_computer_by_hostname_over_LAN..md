---
title: "Connecting to computer by hostname over LAN."
date: 2010-11-22
forum: Networking &amp; Wireless
---

### Post by avada on 2010-11-22
Hi!
I have Ubuntu server installed on my old machine, which has no avahi running. I want to be able to connect to it by hostname. Is it possible. I have a tp-link TL-WR941ND router, but it doesn't seem to have any related options. How can I do it? Is there another way? 

I know I can add them on by one to the host file, but that is not what I want. Also that wouldn't work well with DHCP, and new hosts.

---

### Post by sedawk on 2010-11-22
It is possible but I guess that the software required is
not fully implemented in your router. 

What you basically need is to setup a more powerful
DHCP server and a DNS server in your network. 
This might run on your linux server or on a 
router that supports it (like linux routers).

What you would do is this:
For machines with known MAC address you can tell the DHCP
router to provide a fixed IP address (and therefore also
a fixed DNS name).
So the MAC of your laptop is mapped to a fixed IP which 
is then fixed to a fixed name:
laptop MAC -> 192.168.1.2 -> laptop.example.net
netbook MAC -> 192.168.1.2 -> netbook.example.net
vcr MAC -> 192.168.1.2 -> netbook.example.net

Unknown machines will get IPs from a second pool of addresses:
1st unknown MAC -> 192.168.1.101 -> pool1.example.net
2nd unknown MAC -> 192.168.1.102 -> pool2.example.net

As your DHCP/DNS server also tells all machines in the network
to use the DNS, all machines in the local network should be
able to understand hostnames like the long netbook.example.net
or the short version netbook now!

But as you need additional software on your server or router,
avahi might be an easier option!

---

### Post by avada on 2010-11-22
> **sedawk said:**
> It is possible but I guess that the software required is
not fully implemented in your router. 

What you basically need is to setup a more powerful
DHCP server and a DNS server in your network. 
This might run on your linux server or on a 
router that supports it (like linux routers).

What you would do is this:
For machines with known MAC address you can tell the DHCP
router to provide a fixed IP address (and therefore also
a fixed DNS name).
So the MAC of your laptop is mapped to a fixed IP which 
is then fixed to a fixed name:
laptop MAC -> 192.168.1.2 -> laptop.example.net
netbook MAC -> 192.168.1.2 -> netbook.example.net
vcr MAC -> 192.168.1.2 -> netbook.example.net

Unknown machines will get IPs from a second pool of addresses:
1st unknown MAC -> 192.168.1.101 -> pool1.example.net
2nd unknown MAC -> 192.168.1.102 -> pool2.example.net

As your DHCP/DNS server also tells all machines in the network
to use the DNS, all machines in the local network should be
able to understand hostnames like the long netbook.example.net
or the short version netbook now!

But as you need additional software on your server or router,
avahi might be an easier option!

Thanks for the info!

---

### Post by Iowan on 2010-11-22
I have **DNSMasq** for my network DHCP/DNS. It seems to work fine for connecting DHCP with DNS - my DHCP clients can ping other DHCP clients by name - as well as some static leased machines (like the printer).

---

