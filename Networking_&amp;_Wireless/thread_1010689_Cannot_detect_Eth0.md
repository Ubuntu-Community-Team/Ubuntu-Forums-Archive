---
title: "Cannot detect Eth0"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by zdog291 on 2008-12-14
Okay so I did a fresh install of xubuntu 8.04.1 onto an old dell dimension 4500 and everything works great except for the internet, when I go into network manager you can't create any new connections and when I tried sudo dhclient eth0 it gives an error stating eth0 was not a device found,

---

### Post by Iowan on 2008-12-14
Post results of *ifconfig -a*. **lspci**, and contents of /etc/network/interfaces. I have a Dell Dimension 4100... but it's still on 7.10 (Ubuntu).

---

### Post by zdog291 on 2008-12-14
ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)


lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 11)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 11)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)

auto lo 
iface lo inet loopback

---

### Post by zdog291 on 2008-12-14
I also don't know if this is related but at start up I see these four errors having to do with pci and header types:
[   10.585771] PCI: device 0000:02:00.0 has unknown header type 08, ignoring.
[   10.585842] PCI: device 0000:02:01.0 has unknown header type 7f, ignoring.
[   10.585906] PCI: device 0000:02:02.0 has unknown header type 08, ignoring.
[   10.585983] PCI: device 0000:02:0c.0 has unknown header type 08, ignoring.

I have 3 ethernet cards attached in the pci lots two cnet 200wls and one netgear card. as far as i can tell all of them are not detected

---

### Post by zdog291 on 2008-12-14
I swapped out one of the two cnet ethernet cards for a SMB one, here are the new results of the test, If you notice there is one less uknownheader, but still no recognition

ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1400 (1.3 KB)  TX bytes:1400 (1.3 KB)



lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 11)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 11)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)

auto lo 
iface lo inet loopback


[   10.573548] PCI: device 0000:02:00.0 has unknown header type 08, ignoring.
[   10.573619] PCI: device 0000:02:01.0 has unknown header type 7f, ignoring.
[   10.573699] PCI: device 0000:02:0c.0 has unknown header type 08, ignoring.

---

### Post by zdog291 on 2008-12-16
Any help?

---

### Post by Ben Page on 2008-12-17
No help, sorry, but I wanted to report my problem here ,too.
I also have strange problems with internet and recognition of Eth0. Though when I boot Ubuntu 8.10, my connection is recognized, but after some time, 2, 3 hrs, my internet just stop working without any notification and it cant be started in any way, but by restarting the system. When I search for network - Eth0, it just does something for like a minute, but then stops and say: no wired network available.
It seems like there is some serious issues with detecting and functioning of Eth0 - network in ubuntu/xubunt etc...
Please someone, address to this issue!

---

### Post by zika on 2008-12-17
***_to Ben Page_***
post Your **/etc/network/interfaces** and **/etc/resolv.conf**

first one should look like this:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface DHCP
auto eth0
iface eth0 inet dhcp
```and the second:```
nameserver xxx.xxx.xxx.xxx
...
nameserver yyy.yyy.yyy.yyy
nameserver zzz.zzz.zzz.zzz
```that way You won't have Network Manager hoovering all the time and should have stable connection.

---

