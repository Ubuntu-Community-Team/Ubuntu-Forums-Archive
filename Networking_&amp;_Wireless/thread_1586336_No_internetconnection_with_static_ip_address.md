---
title: "No internetconnection with static ip address"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by n0c0d3 on 2010-10-01
Hi,

I'm trying to configure a static ip-address on Xubuntu 10.04. But when I do this my local network is working fine, but I can't access the internet anymore.

I'm using a wired LAN-router. In the Network Manager IPv4 Settings I use the following configuration:
Method: Manual
Address: 192.168.1.100
Netmask: 255.255.255.0
Gateway: 192.168.1.1

The router settings are:
Device IP Address: 192.168.1.1
Subnet mask: 255.255.255.0
WAN connection type: Obtain an IP automatically

This does assign me the correct ip-address when I reset the router, but I loose the internet connection. When I use the Automatic DHCP in the IPv4 Settings all works fine.

Any idea how to setup the network correctly so all connections work and I have a static local ip?

Bart

---

### Post by cj.surrusco on 2010-10-01
> **n0c0d3 said:**
> Hi,

I'm trying to configure a static ip-address on Xubuntu 10.04. But when I do this my local network is working fine, but I can't access the internet anymore.

I'm using a wired LAN-router. In the Network Manager IPv4 Settings I use the following configuration:
Method: Manual
Address: 192.168.1.100
Netmask: 255.255.255.0
Gateway: **92.168.1.1**

The bold should be 192.168.1.1, you forgot the one in the beginning. That would explain why you can't reach the internet.

---

### Post by chili555 on 2010-10-01
Is there an option to specify a DNS nameserver? Did you? I believe you may safely use 192.168.1.1.

---

### Post by n0c0d3 on 2010-10-01
I'm sorry but I made a typo. I've tried it with 192.168.1.1, but I accidentally forgot to type the first '1' in the gateway setting in my post. 

Chilly555.  I didn't set any DNS server in the IPv4 settings. I left that blank. I wouldn't even know what to fill in there. But should I use it somehow?

---

### Post by cj.surrusco on 2010-10-01
> **n0c0d3 said:**
> I'm sorry but I made a typo. I've tried it with 192.168.1.1, but I accidentally forgot to type the first '1' in the gateway setting in my post. 

Chilly555.  I didn't set any DNS server in the IPv4 settings. I left that blank. I wouldn't even know what to fill in there. But should I use it somehow?

You would need to put the DNS servers that your ISP provides for you if you want to access websites by their domain name instead of IP address. You would need to contact your ISP to find out what they are, or it may be located in your router's config (it is for me). Type 192.168.1.1 in a browser and you will be able to access your router config. Take a look around and see if you can find any info on DNS servers.

---

### Post by n0c0d3 on 2010-10-01
Yes, that did the trick. I filled in both DNS server IPs listed and all is working now as I was looking for.

Great!

Thanks guys,
Bart

---

