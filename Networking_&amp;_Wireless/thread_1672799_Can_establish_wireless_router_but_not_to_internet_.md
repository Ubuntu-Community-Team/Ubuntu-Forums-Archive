---
title: "Can establish wireless router but not to internet Ubuntu 10.10"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by programmershope on 2011-01-21
I can establish wireless connection to router. But not to the Internet.

Few details given below:

Ubuntu: 10.10
Wireless driver: Broadcom STA wireless driver.
Status: This device is activated and currently in use.
Wireless mode: Infrastructure
Wireless security: WPA & WPA2 Personal
IPV4 Settings Method: Automatic (DHCP) addresses only.
DNS servers: 8.8.8.8, 8.8.4.4

Tried using Automatic DHCP only.. but no luck.

Thanks in advance...

---

### Post by kgriff on 2011-01-21
Sounds like you may be having the same problem I am.  Run terminal and:
ping -c 5 google.com

Please post result

---

### Post by programmershope on 2011-01-22
> **kgriff said:**
> Sounds like you may be having the same problem I am.  Run terminal and:
ping -c 5 google.com

Please post result

omkar@omkar:~$ ping -c 5 google.com
ping: unknown host google.com

Before posting this thread, i had checked /var/lib/NetworkManager/NetworkManager.state

Previously, this was set as
WirelessEnabled=false

Then I changed this to:
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

Then I ran sudo rfkill unblock all and rebooted but none of this helped.

---

### Post by Cr0n_J0b on 2011-01-22
try turning off security on the router and see if you can get through.  Also, is your router setup with DHCP?  do you have an IP on the linux box?  try.

ifconfig

netstat -rn

and post up.

If I were a betting man, it's either DHCP or security.

---

### Post by programmershope on 2011-01-22
> **Cr0n_J0b said:**
> try turning off security on the router and see if you can get through.  Also, is your router setup with DHCP?  do you have an IP on the linux box?  try.

ifconfig

netstat -rn

and post up.

If I were a betting man, it's either DHCP or security.

omkar@omkar:/var/lib/NetworkManager$ ifconfig
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:81:c4:51  
          inet6 addr: fe80::f24d:a2ff:fe81:c451/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8098 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5437 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4922958 (4.9 MB)  TX bytes:1001284 (1.0 MB)
          Interrupt:45 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 78:e4:00:89:10:ea  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7ae4:ff:fe89:10ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:356 errors:0 dropped:0 overruns:0 frame:6348
          TX packets:493 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:291174 (291.1 KB)  TX bytes:69150 (69.1 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77113 (77.1 KB)  TX bytes:77113 (77.1 KB)

omkar@omkar:/var/lib/NetworkManager$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth1

---

