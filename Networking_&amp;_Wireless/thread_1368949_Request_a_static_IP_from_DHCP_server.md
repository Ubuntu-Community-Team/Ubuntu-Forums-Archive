---
title: "Request a static IP from DHCP server ?"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by pstein on 2009-12-31
Currently at each start a new dynamic IP is assigned from the DHCP server to my local Ubuntu installation.
 
I want to prevent this.
 
Can I somehow forece (or at least suggest) the DCHP server a certain IP?
I have no acces to DHCP server but would like to ask the DHCP server:
"Please could you give me IP 192.168.0.77"
 
How do I have to setup this request-for-IP?
 
peter

---

### Post by kevinatkins on 2009-12-31
Yes, it is possible, but we need to know what is acting as the DHCP server on your network? Is it your modem / router, or do you have a machine running a DHCP server? Either way, you are going to need administrative access to the server to set things up....

---

### Post by focwiz on 2009-12-31
> **pstein said:**
> Currently at each start a new dynamic IP is assigned from the DHCP server to my local Ubuntu installation.
 
I want to prevent this.
 
Can I somehow forece (or at least suggest) the DCHP server a certain IP?
I have no acces to DHCP server but would like to ask the DHCP server:
"Please could you give me IP 192.168.0.77"
 
How do I have to setup this request-for-IP?
 
peter

This is probably easiest to accomplish by NOT using DHCP, rather setting up your machine with a static ip address. easy to do, but you need to know;

1. an available address for your machine (usually one outside of the dhcp assigned range
2. the netmask (typically 255.255.255.0)
3. The gateway device (typically the ip address of the router)
4. DNS server addresses (either use the same ones you get assigned by dhcp, or use OpenDNS servers available fro OpenDNS.com

In your network connection screen, simply select "manual" rather than dhcp

---

### Post by Iowan on 2009-12-31
Just so you have a bewildering assortment of choices...
Check **man dhclient.conf** page. I seem to remember an option to request an address.

I found some information on **option dhcp-requested-address ip-address;** in **man dhcp-options** It doesn't seem to work on my machine, though.

---

