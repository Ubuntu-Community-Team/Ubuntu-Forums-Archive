---
title: "Server loses static address"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by jowilkin on 2008-12-20
I have a server running Ubuntu 8.10 server, 64-bit.  It is set to use a static ip address.

It will work for a while with this static address, but then after a while (less than 24 hours), I will try to log in with SSH and am unable to connect.  If I check to the server it then seems to have an IP address from DHCP instead of the static one.

If I restart networking, then the static IP address is reinstated and I can connect to the server again.  This will work for a while and invariably the server will again lose the static IP and fall back to the dynamic one.

Here is my /etc/network/interfaces file, the problem is on eth1, eth0 is being used as a DHCP server for a private network and that seems to be working without a problem:

> # The loopback network interface
auto lo
iface lo inet loopback

# Private Network ethernet device
auto eth0
iface eth0 inet static
        address 192.168.0.1
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255

# The primary network interface
auto eth1
iface eth1 inet static
        address 129.170.65.234
        netmask 255.255.252.0
        network 129.170.64.0
        broadcast 129.170.67.255
        gateway 129.170.64.1


Here is the output of ifconfig (when it is working correctly):
> eth0      Link encap:Ethernet  HWaddr 00:18:8b:4d:8d:4e  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:fe4d:8d4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:536 errors:0 dropped:0 overruns:0 frame:0
          TX packets:234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62658 (62.6 KB)  TX bytes:31139 (31.1 KB)
          Interrupt:16 Memory:f8000000-f8012700 

eth1      Link encap:Ethernet  HWaddr 00:18:8b:4d:8d:50  
          inet addr:129.170.65.234  Bcast:129.170.67.255  Mask:255.255.252.0
          inet6 addr: fe80::218:8bff:fe4d:8d50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12696 errors:0 dropped:0 overruns:0 frame:0
          TX packets:268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1471482 (1.4 MB)  TX bytes:58524 (58.5 KB)
          Interrupt:16 Memory:f4000000-f4012700 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:810 errors:0 dropped:0 overruns:0 frame:0
          TX packets:810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56906 (56.9 KB)  TX bytes:56906 (56.9 KB)


I've poked around everywhere I can think of and searched online, and I can't figure out what's going on here.  Any advice would be much appreciated.

Thanks,
John

---

### Post by cariboo on 2008-12-20
I removed dhcp3-client, and now have no problems with my static ip address. I was running into the same problem, with a static ip address you don't need the dhcp client.

Jim

---

### Post by jowilkin on 2008-12-20
> **cariboo907 said:**
> I removed dhcp3-client, and now have no problems with my static ip address. I was running into the same problem, with a static ip address you don't need the dhcp client.

Jim

Thanks for the advice, I removed the dhcp client and will see if that resolves the problem.

---

### Post by Iowan on 2008-12-20
Another option is to have the DHCP issue the server a static lease (IP based on MAC address).

---

### Post by jowilkin on 2008-12-21
> **Iowan said:**
> Another option is to have the DHCP issue the server a static lease (IP based on MAC address).

Thanks for the advice, that would probably work, but I think this may not be an option as I don't have control of the DHCP server. It is administered by my institution and I administer a small private network within the institution.

---

### Post by jowilkin on 2008-12-26
Well removing the dhcp client seems to have worked, but seems really messy to me...

---

### Post by Iowan on 2008-12-27
I suppose *disabling* dhclient (via rc.X) would have been another option, but still messy.

---

