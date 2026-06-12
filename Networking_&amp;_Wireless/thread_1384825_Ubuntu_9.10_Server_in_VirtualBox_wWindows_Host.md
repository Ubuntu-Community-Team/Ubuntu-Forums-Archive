---
title: "Ubuntu 9.10 Server in VirtualBox w/Windows Host"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by StevenC68 on 2010-01-18
Hi Everyone,

I have Ubuntu 9.10 Server on a Windows Host in Sun VirtualBox.  

The Ubuntu Server is not configured as a DHCP Server
The Ubuntu Server's primary interface (eth0) is inet dhcp

when this virtual machine boots - it comes on a 10.0.2.* network.

my home network is pretty standard, ISP modem as dhcp - on a normal 192.168.*.* network.  

I have attempted to modify /etc/network/interfaces to include:

# The primar network interface
auto eth0
iface eth0 inet static
    ????
    ????
    ????

I have done the above (IP's ommited) a couple different ways, but when the system reboots (it does have the static ip and bcast info correct, meaning 192.168.0.x and 255.255.255.0) I cannot ssh, ping, telnet <see> the virtual server nor can the virtual server see the host IP (192.168.0.x).

yes, I'm a newb - but please help point me in the right direction in either case :).



Thanks,

Steve

---

### Post by pirateghost on 2010-01-18
> **StevenC68 said:**
> Hi Everyone,

I have Ubuntu 9.10 Server on a Windows Host in Sun VirtualBox.  

The Ubuntu Server is not configured as a DHCP Server
The Ubuntu Server's primary interface (eth0) is inet dhcp

when this virtual machine boots - it comes on a 10.0.2.* network.

my home network is pretty standard, ISP modem as dhcp - on a normal 192.168.*.* network.  

I have attempted to modify /etc/network/interfaces to include:

# The primar network interface
auto eth0
iface eth0 inet static
    ????
    ????
    ????

I have done the above (IP's ommited) a couple different ways, but when the system reboots (it does have the static ip and bcast info correct, meaning 192.168.0.x and 255.255.255.0) I cannot ssh, ping, telnet <see> the virtual server nor can the virtual server see the host IP (192.168.0.x).

yes, I'm a newb - but please help point me in the right direction in either case :).



Thanks,

Steve

in your VirtualBox VM settings, set the nic to BRIDGE instead of NAT

---

### Post by StevenC68 on 2010-01-18
Thanks!  That got me started, now when I'm booted up I only see an IPV6 address and not an ipv4...

I'll do some searching and see what I find there.


Best Regards, 

Steve

---

