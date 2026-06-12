---
title: "cannot access the internet using Manaul in the  IPv4 Settings"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by wstay on 2009-03-13
I connect using the Automatic (DHCP) in the IPv4 Settings and I can access the Internet. But when I change to Manual in the  IPv4 Settings I cannot access the Internet though my modem shows it is connected.
I use the following configuration for my Manual setting in the IPv4 Settings: Address: 192.168.1.3
          Netmask: 255.255.255.0
          Gateway: 192.168.1.1
          DNS Servers: 202.188.1.133, 202.188.0.5
So what is preventing me from accessing the Internet using my Manual configuration? Can someone please help.

---

### Post by Mach1US on 2009-03-14
> **wstay said:**
> I connect using the Automatic (DHCP) in the IPv4 Settings and I can access the Internet. But when I change to Manual in the  IPv4 Settings I cannot access the Internet though my modem shows it is connected.
I use the following configuration for my Manual setting in the IPv4 Settings: Address: 192.168.1.3
          Netmask: 255.255.255.0
          Gateway: 192.168.1.1
          DNS Servers: 202.188.1.133, 202.188.0.5
So what is preventing me from accessing the Internet using my Manual configuration? Can someone please help.

Personally i had to :
sudo apt-get remove network-manager
than configure all addresses from command line.
Now works perfect.

---

### Post by wstay on 2009-03-15
> **Mach1US said:**
> Personally i had to :
sudo apt-get remove network-manager
than configure all addresses from command line.
Now works perfect.

Thanks for the advice.
I got it working now.
My DNS Servers which is my ISP should be 202.188.0.133, 202.188.1.5 and not 202.188.1.133, 202.188.0.5.
However my TP-Link TD-8800 ADSL modem connecting via a Desktop switch does not support Autonatic (DHCP). It does however support manual configuration.

---

