---
title: "Help configuring two nework interfaces."
date: 2010-09-23
forum: Networking &amp; Wireless
---

### Post by af.at.work on 2010-09-23
I have got two NICs configured on a VM - each is tied to a specific network, one is a DMZ, the other is an internal network.
 
I want to let MySQL listen on the internal network only, that is working now... I want Apache on the DMZ with http and https but as soon as I add the second interface I run into trouble. I can't hit any of the allowed TCP ports (80,443)... I can't ping it... nothing.
 
Here's the config... which now after removing the gateway from the private network seems to be working.. could someone sanity check this please?
 
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
address 10.153.24.230
netmask 255.255.255.240
network 10.153.24.224
broadcast 10.153.24.239
# gateway 10.153.24.225
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 8.8.8.8
auto eth1
iface eth1 inet static
address 10.153.24.195
netmask 255.255.255.224
# network 10.153.24.192
gateway 10.153.24.193
broadcast 10.153.23.223
# dns-nameservers 8.8.8.8

---

### Post by af.at.work on 2010-09-23
OK. Spoke too soon. HTTP is working on both interfaces, but I can no longer get to MySQL on any interface.

---

### Post by mightymouse2045 on 2010-09-23
ummm you have the networks etc setup incorrectly.

Let me get this straight - you want an internal network and a DMZ network right?

Your broadcast should be 10.153.24.223 for eth1 and you have commented out your network which is correct so not sure why?

You will need to setup nats and routes for each network also and why have you commented out your gateway on eth0?

Basically keep the two network ranges completely separate. your 10.x.x.x network can be your internal network and your DMZ should be something like 172.16.x.x or basically a completely different class. They are both internal so it doesn't matter but best practice and less headaches etc 

Something like this:

# The primary network interface (Internal)
auto eth0
iface eth0 inet static
address 10.153.24.230
netmask 255.255.255.240
network 10.153.24.224
broadcast 10.153.24.239
gateway 10.153.24.225

# DMZ Interface
 auto eth1
 iface eth1 inet static
 address 172.16.0.6
 netmask 255.255.255.224 (30 hosts?!? maybe do .240 for 14 hosts)
 network 172.16.0.0
 gateway 172.16.0.1
 broadcast 172.16.0.31 (or .15 if you have .240 subnet)

Your name servers should be put into /etc/resolv.conf by the way 
nameserver 8.8.8.8
domain yours.local
search yours.local

How these are routed and handle requests etc depend on how vlans/switches/routers etc are setup what else is in the picture?

---

### Post by af.at.work on 2010-09-23
Thanks for the reply. 
 
Unfortunately, I have no control over the two networks that I am provided by my ISP in their VMware enviroment.
 
10.153.24.224/28 (Internal)
10.153.24.192/27 (DMZ)
 
Only IP addresses in the DMZ can be tied to public IP addresses.
 
Ideally, this server will be able to communicate with another server on the internal network. It will also act as a web server in the DMZ.

---

### Post by mightymouse2045 on 2010-09-24
> **af.at.work said:**
> Thanks for the reply. 
 
Unfortunately, I have no control over the two networks that I am provided by my ISP in their VMware enviroment.
 
10.153.24.224/28 (Internal)
10.153.24.192/27 (DMZ)
 
Only IP addresses in the DMZ can be tied to public IP addresses.
 
Ideally, this server will be able to communicate with another server on the internal network. It will also act as a web server in the DMZ.

Ok so make the changes as this then:

# The primary network interface (Internal)
auto eth0
iface eth0 inet static
address 10.153.24.230
netmask 255.255.255.240
network 10.153.24.224
broadcast 10.153.24.239
gateway 10.153.24.225

# DMZ Interface
 auto eth1
 iface eth1 inet static
 address 10.153.24.195
 netmask 255.255.255.224
 network 10.153.24.192
 gateway 10.153.24.193
 broadcast 10.153.24.223

 EDIT - /etc/resolv.conf 
nameserver 8.8.8.8

The above is the correct way to setup your nics. However you should also have access to switches (virtual or physical) and have separate VLans setup one for DMZ and one for internal network. Your internal? clients will have the 10.153.24.230 as their gateway, and your server should NAT all requests from your internal to your DMZ network.

As for your services running on this box you want SQL and Apache to both be listen on the INTERNAL network IP ONLY! Then what you need to do is setup a static NAT or PAT for your internal to DMZ networks. This way you have access control and things are more secure that way.

eg 

static 10.153.24.230 is nat'd to 10.153.24.195 so all ports are open to the internet (unwise unless you have hardware firewalls in place and then still not best practice

PAT 10.153.24.230 ports 80,443,etc are nat'd to 10.153.24.195 ports 80,443,etc
This way ONLY the ports you need to be available externally are nat'd.

You can do this with a basic firewall app like IPTables. IPTables also has a GUI you can install to manage it

---

