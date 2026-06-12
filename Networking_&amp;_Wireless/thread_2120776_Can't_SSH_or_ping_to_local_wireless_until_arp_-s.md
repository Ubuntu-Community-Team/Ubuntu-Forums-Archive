---
title: "Can't SSH or ping to local wireless until arp -s"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by ckrosco on 2013-02-27
When I first boot my laptop with a wireless connection, it is not accessible to other local computers using ssh or ping.

However, if the same laptop boots with an ethernet connection, ssh and ping work correctly.

In both cases, the laptop can access the WAN.

I can only access the wireless laptop if I issue an arp command:

arp -s 192.168.1.5 AA:BB:CC:dd:EE:FF

After that, ssh and ping work as expected.

What could be preventing the wireless interface from broadcasting its MAC address?

---

### Post by papibe on 2013-02-27
Hi ckrosco. Welcome to the forums ):P

My first guess would be to check your router:
[LIST]
[*]Are the wired network and wireless network in the same IP range?
[*]Does the laptop has set an static IP or a DHCP reservation using its ethernet MAC?
[/LIST]
Then, from the other computers:
[LIST]
[*]Does the laptop appear with another MAC on the arp table (arp -v), or it does not appear at all?
[/LIST]

Regards.

---

### Post by ckrosco on 2013-02-27
> **papibe said:**
> Are the wired network and wireless network in the same IP range?
Yes, all devices are within 192.168.1.1 - 192.168.1.10
> Does the laptop has set an static IP or a DHCP reservation using its ethernet MAC?Laptop has a static IP - 192.168.1.5. I use the same IP address for both the wired and wireless laptop connection, which automatically switches depending on whether there's a cable attached.
> Does the laptop appear with another MAC on the arp table (arp -v), or it does not appear at all?The laptop does not appear in the arp table until I do a PING (which does not respond), then I see:

```
arp -v
Address                  HWtype  HWaddress           Flags Mask            Iface
laptop                           (incomplete)                              eth0
```Here is the ifconfig from the laptop:

```
ifconfig
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:82ff:fe94:4817/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1161632 errors:116 dropped:0 overruns:0 frame:522662
          TX packets:795356 errors:77 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1688142507 (1.6 GB)  TX bytes:65040986 (65.0 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34553 (34.5 KB)  TX bytes:34553 (34.5 KB)
```I used the HWaddr from eth1 in my arp command  

arp -s 192.168.1.5 AA:BB:CC:dd:EE:FF

to gain access to the laptop, but without that manual entry into the arp table, I can't connect to the laptop.

---

### Post by papibe on 2013-02-27
Thanks.

Is that the static IP defined on the router or the laptop itself?
Is your router your DHCP server?

Regards.

---

### Post by ckrosco on 2013-02-27
> **papibe said:**
> Is that the static IP defined on the router or the laptop itself?
Is your router your DHCP server?

Thanks for your speedy replies.

I've turned DHCP off. The ADSL modem has a setting to reserve IP addresses, but I think it's not necessary. But I have the laptop IP address set there.

I have a ADSL modem connected to a switch, which is connected to a wireless router as a WAP. Should the wireless router have a setting for the laptop IP address?

I believe the definition for the laptop IP address comes from the laptop itself, using the network manager GUI. 

The laptop /etc/network/interface file has this:

```
auto lo
iface lo inet loopback
```Although in trying to sort out this problem I also tried this:

```
auto eth1
 iface eth1 inet static 
address 192.168.1.5 
netmask 255.255.255.0 
broadcast 192.168.1.255 
gateway 192.168.1.1 
dns-nameservers 8.8.8.8 192.168.1.1
```Which didn't improve things, so I deleted that section.

---

