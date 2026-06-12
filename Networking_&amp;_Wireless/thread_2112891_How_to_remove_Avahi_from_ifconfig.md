---
title: "How to remove Avahi from ifconfig"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by tlotr on 2013-02-06
Hi,

Please help me in removing eth0 avahi from the ifconfig command. I want the eth0 to have a IPv4 address and not the eth0 avahi.

Below is the details of the ifconfig command:

eth0      Link encap:Ethernet  HWaddr fc:75:16:e1:1d:1b  
          inet6 addr: fe80::fe75:16ff:fee1:1d1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88372 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33915 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32591941 (32.5 MB)  TX bytes:4587460 (4.5 MB)

eth0:avahi Link encap:Ethernet  HWaddr fc:75:16:e1:1d:1b  
          inet addr:169.254.5.64  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21925 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21925 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8990795 (8.9 MB)  TX bytes:8990795 (8.9 MB)

In the /etc/network/interfaces I am using the following

auto eth0
iface eth0 inet dhcp

When the system start, Ubuntu shows trying to get network information and then shows the message that its booting without it.

In windows the ip address is automatically added to the NIC through DHCP but the same is not happening in Ubuntu

---

### Post by tlotr on 2013-02-19
Hi All,

This is resolved now. This is what I have done to resolve the issue.

I edited the interfaces file from /etc/network/ and the below edition. I made the iface eth0 inet static from dhcp and below i added the same ip address which was being assigned as the avahi and it works now. Now if I do the ifconfig in terminal it shows that eth0 is having the ip address and there is no avahi show in ifconfig. Also the system boots faster now as there is no message at the start which shows trying to get the network configuration/information.

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static

address 169.254.5.64
netmask 255.255.0.0
broadcast 169.254.5.255

---

### Post by bab1 on 2013-02-19
> **tlotr said:**
> Hi All,

This is resolved now. This is what I have done to resolve the issue.

I edited the interfaces file from /etc/network/ and the below edition. I made the iface eth0 inet static from dhcp and below i added the same ip address which was being assigned as the avahi and it works now. Now if I do the ifconfig in terminal it shows that eth0 is having the ip address and there is no avahi show in ifconfig. Also the system boots faster now as there is no message at the start which shows trying to get the network configuration/information.

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static

address 169.254.5.64
netmask 255.255.0.0
broadcast 169.254.5.255

Why did you do that?  That IP address is for 'link local' only (LAN).  It is not a valid address to surf the Internet with.  Your router will grump about that...

Edit:  The reason you got that address at all was because eth0 was not configured with a DHCP supplied IP address.  Is there a functioning DHCP server?

---

### Post by tlotr on 2013-02-19
Hi Bab1,

I do not use a router. I have internet using PPPoE which is configured on the system and is having a separate IP address to access the internet.

---

