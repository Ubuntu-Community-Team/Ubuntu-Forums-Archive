---
title: "Static IP on machine"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by PimPamPum on 2009-01-27
I'm trying to get my IP static on my ubuntu intrepid machine , i changed the /etc/network/interfaces file to :

auto lo
iface lo inet loopback

allow-hotplug eth0
iface eth0 inet static
       address 192.168.1.33
       netmask 255.255.255.0
       gateway 192.168.1.1


Still the IP never comes 192.168.1.33, am i doing something rong ?
My machine is connected to a router on DHCP.

---

### Post by jonobr on 2009-01-27
hello


could you post the results of ifconfig

---

### Post by zika on 2009-01-27
> **PimPamPum said:**
> I'm trying to get my IP static on my ubuntu intrepid machine , i changed the /etc/network/interfaces file to :

auto lo
iface lo inet loopback

allow-hotplug eth0
iface eth0 inet static
       address 192.168.1.33
       netmask 255.255.255.0
       gateway 192.168.1.1


Still the IP never comes 192.168.1.33, am i doing something rong ?
My machine is connected to a router on DHCP.
try with:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
       address 192.168.1.33
       netmask 255.255.255.0
       gateway 192.168.1.1
```

---

### Post by PimPamPum on 2009-01-27
I tried this :

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
       address 192.168.1.33
       netmask 255.255.255.0
       gateway 192.168.1.1


and curiously it changed the device do eth1 still with no static ip,
my ifconfig commnand now looks like this :

eth1      Link encap:Ethernet  HWaddr 00:e0:4d:81:e3:85  
          inet addr:192.168.1.37  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe81:e385/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1135317 errors:0 dropped:0 overruns:0 frame:0
          TX packets:601529 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1410721353 (1.4 GB)  TX bytes:138556397 (138.5 MB)
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:570 errors:0 dropped:0 overruns:0 frame:0
          TX packets:570 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:49032 (49.0 KB)  TX bytes:49032 (49.0 KB)

Is this worst or just diferent ?

---

### Post by Coreigh on 2009-01-27
On the basic Ubuntu (Gnome desktop) I click on the network icon in the upper panel and choose "Manual Configuration" to set a static IP. No editing of files directly. You can also go to System >> Administration >> Network and unlock the config and disable "Roaming Mode" to set a static IP.

---

