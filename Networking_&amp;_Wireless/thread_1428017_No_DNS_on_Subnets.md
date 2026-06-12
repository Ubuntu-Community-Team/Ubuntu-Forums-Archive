---
title: "No DNS on Subnets"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by Monotoba on 2010-03-12
Hi All,


I realize my issue is a network issue and not actually related to Ubuntu. But since I use Ubuntu and find that *nix users are the smartest and most active out there in forum land, I am asking for help here.

I have a class C network composed of one cable modem (road runner) A Cisco 2100. I also have four routers. The routers are set up as subnets. I'm not a network guy so I think I have something setup wrong. I have dns only on the router that is plugged into the cable modem. All subnets have no dns but can connect using ip addresses to both internal and external sites and devices. 

I need to know first if the DNS for the subnets should point to the external DNS service or to the router that is directly connected to the cable modem. Second, do I use a single router's DHC server or configure each router to serve only it's own allotted ip address (this is how I have it now)?

The way I have things set up is router #1 has the other three routers directly connected. The router settings are:

Router 1:
WAN: Dynamic

LAN
Ip: 192.168.1.1
Mask: 255.255.255.192
DNS: 209.18.47.61 and 62


Router 2:
Wan:
Ip: 192.168.1.2

Lan:
Ip: 192.168.1.64
Mask: 255.255.255.192
DNS: 192.168.1.1

Router 3:
Wan: 192.168.1.3

LAN: 192.168.1.128
Mask: 255.255.255.192
DNS: 192.168.1.1

Router 4:
WAN: 192.168.1.4

Lan: 192.168.1.192
Mask: 255.255.255.192
DNS: 192.168.1.1

Thanks for your help!

---

### Post by helgman on 2010-03-12
Hi,

> **Monotoba said:**
> I need to know first if the DNS for the subnets should point to the external DNS service or to the router that is directly connected to the cable modem.

Either one should work - want you don't want (or what I wouldn't want anyway) is the client to first ask their closest router that asks the one connected to the modem that asks ... Just to many steps. Set the router connected to Internet as the DNS server or set the external DNS.

> Second, do I use a single router's DHC server or configure each router to serve only it's own allotted ip address (this is how I have it now)?

Depends on what options you have. The important thing is that your clients get IP addresses related to their subnets - who services is doesn't really mater as long as it's handing out (the right) IP addresses.

I would have the local routers acting as DHCP servers for their local subnets so that I don't lose DHCP if one of the other routers goes off line. But if your routers support it you could set one router (the one connected to the Internet) to serve IP address to all clients since that might make the DNS part simpler - just make sure to serve the correct settings to each subnet so the gateway and whatnot correspond to that particular subnet). And point the client DNS to either 192.168.1.1 (and make sure the local DHCP servers give them that address) or point them to your external DNS.

Hope you get it up and running.

Regards,
Helgman

---

### Post by Monotoba on 2010-03-12
Thank you, I have been unable to get the DNS on the subnets but Im starting to wonder if it could be the router. Everything you said made sense to me. So I'm wondering what would cause me to be able to access everything inside and outside the LAN via IP but not with the domain name. The way I see it the routers should pass the DNS request up to Router 1 or the external router. But that is not happening on the subnets. Perhaps this is an issue with the Belkin router I am using for Router 1. I did have an issue resetting it to factory defaults. It cleared the most WAN and LAN settings but not all of them. I had to access the router via the control panel and use the option there to clear all settings. Just to get it to speak to the cable modem. The hardware switch was not working.

Thanks for your help. I think I understand the basic of subnetting. But I only have a basic understanding. 

Again, thank you.

---

### Post by bab1 on 2010-03-12
> **Monotoba said:**
> Hi All,


I realize my issue is a network issue and not actually related to Ubuntu. But since I use Ubuntu and find that *nix users are the smartest and most active out there in forum land, I am asking for help here.

I have a class C network composed of one cable modem (road runner) A Cisco 2100. I also have four routers. The routers are set up as subnets. 
This is a little vague.  What is the cisco 2100?  Is it a [**_Catalyst switch_**]("http://www.cisco.com/en/US/products/hw/switches/ps591/tsd_products_support_eol_series_home.html") or a [**_wireless LAN controller_**]("http://www.cisco.com/en/US/prod/collateral/wireless/ps6302/ps8322/ps7206/ps7221/product_data_sheet0900aecd805aaab9.html")?  The topology is important in making decisions with network design.
> 
I'm not a network guy so I think I have something setup wrong. I have dns only on the router that is plugged into the cable modem. 
What router is that? Can you provide a diagram?> 
All subnets have no dns but can connect using ip addresses to both internal and external sites and devices. 
The IP subnets don't need a DNS server in their part of the LAN.  The DNS server they query can be anywhere.  If you are providing LAN side DNS (with private addressing) you will need to configure the LAN side DNS server and point all hosts in the LAN to that server.  

Here  is how I do it.  I have a router that is the Gateway for my lan (eg it is directly connected (DC) to WAN on one side and LAN on the other.  This provides all the DNS for the LAN and refers all WAN side requests to the DNS server I selected on the Internet.  All hosts in the LAN have the address of the Gateway (it's a router) @192.168.1.1 for DNS. The IP address for a secondary DNS server is configured on each host also.  This is in case the  primary DNS service is unavailable. 

DNS does NOT refer the host upstream as you might think.  If DNS server is contacted and can't answer the query, it is referred to the root server of the particular domain (i.e. com, org, net, uk, etc) for resolution.  Your DNS server then caches that info for some time for later use.

I only have one DNS server in my LAN. If you a large enough LAN that you feel you have a need for primary and secondary DNS servers then I would look into BIND9 or at the very least DNSmasq.
> 

I need to know first if the DNS for the subnets should point to the external DNS service or to the router that is directly connected to the cable modem. 

Are you going to host LAN side DNS?  If yes then you should point all LAN hosts to the routers DNS server.  The routers DNS server will refer all external queries like I described above.
> 
Second, do I use a single router's DHC server or configure each router to serve only it's own allotted ip address (this is how I have it now)?


You will need a DHCP server in each area that has a distinct IP address range.  DHCP servers use a pool of IP addresses.  They can't differentiate between subnets as you described.

Personally I think you are better off with VLAN's and one DHCP server for the entire LAN.  If you feel you need a backup you can have that with alternative numbering such as DHCP1 has 1 - 99 and DHCP has 100 -200.  That way if one goes down you still have DHCP services.

---

