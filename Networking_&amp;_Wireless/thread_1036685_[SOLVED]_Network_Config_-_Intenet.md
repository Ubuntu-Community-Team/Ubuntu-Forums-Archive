---
title: "[SOLVED] Network Config - Intenet"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by anjanesh on 2009-01-11
Hi

I just installed Kubuntu on a PC in a LAN.
But Im unable to connect to the internet.
ping 192.168.1.* works but ping google.com returns unknown host.

I have this in my /etc/network/interfaces
```
#eth0 main
auto eth0
iface eth0 inet dhcp

auto lo
iface loopback inet loopback
```Is there something Im missing ?

```
user@mypc:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
user@mypc:~$
```
 


Thanks

---

### Post by Iowan on 2009-01-11
Try ```
ping 209.85.171.100
``` If that works, you *probably* have a DNS problem.  (Unfortunately, I don't have IP addresses for OpenDNS at my fingertips).

---

### Post by anjanesh on 2009-01-11
Im not at the Kubuntu machine now, but I'll check tomorrow morning.
But if it does work, then what do I have to modify? Add nameservers in /etc/resolv.conf ?

The LAN is connected to a router for which the default gateway is 192.168.1.1 which I added in /etc/network/interfaces

```
#eth0 main
auto eth0
iface eth0 inet dhcp
gateway 192.168.1.1
```

---

### Post by Iowan on 2009-01-11
DNS addresses should *probably* be set up on router - which would inform DHCP clients. [This]("http://ubuntuforums.org/showpost.php?p=6510814&postcount=2") post mentions a couple of addresses. [Wikipedia]("http://en.wikipedia.org/wiki/OpenDNS") lists four:>     * 208.67.222.222 (resolver1.opendns.com)
    * 208.67.220.220 (resolver2.opendns.com)
    * 208.67.222.220
    * 208.67.220.222


---

### Post by albinootje on 2009-01-11
> **anjanesh said:**
>  But if it does work, then what do I have to modify? Add nameservers in /etc/resolv.conf ?


I think Kubuntu, just like Ubuntu, uses Network Manager.
That means you have at least a few choices :

1) Use Network Manager to let N.M. do the content of /etc/resolv.conf
2) Remove Network Manager in case you want "the full control" with a customized /etc/network/interfaces and /etc/resolv.conf
3) Remove Network Manager, and use wicd, [http://wicd.sf.net](http://wicd.sf.net)

Try option 1 first.
And please post the output of 
```

cat /etc/resolv.conf

```

---

### Post by anjanesh on 2009-01-12
Odd ! ping 209.85.171.100 works ! 209.85.171.100 shows up google page on konqueror !

```
~$cat /etc/resolv.conf
nameserver 192.168.1.1

~$cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

~$route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
```

---

### Post by anjanesh on 2009-01-12
Solved.
I edited /etc/dhcp3/dhclient.conf
and uncommented **prepend domain-name-servers** and added the DNS servers here.

---

### Post by albinootje on 2009-01-12
> **anjanesh said:**
> Solved.
I edited /etc/dhcp3/dhclient.conf
and uncommented **prepend domain-name-servers** and added the DNS servers here.

Good. Interesting solution! :)

Please mark this thread as SOLVED, thanks.

---

### Post by anjanesh on 2009-01-12
On the Windows PCs which are on the same LAN, the DNS servers mentioned on all Windows PCs are
```
203.xx.xxx.70
203.xx.xxx.70
```
While the DNS servers mentioned in the router is
```
203.xx.xxx.1
203.xx.xxx.1
```
So Im guessing that the DNS in the router is wrong and should've been 203.xx.xxx.70 instead of 203.xx.xxx.1.

---

