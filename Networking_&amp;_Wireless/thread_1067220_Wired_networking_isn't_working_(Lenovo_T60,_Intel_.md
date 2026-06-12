---
title: "Wired networking isn't working (Lenovo T60, Intel 82573L gigabit chipset)"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by thewise1 on 2009-02-11
I'm trying to run Ubuntu on my work laptop (with vmware workstation to handle an XP virtual machine).

I've installed 8.10 on the laptop, clean install.

The laptop is a Lenovo T60, using the Intel 82573L gigabit ethernet chipset. It does not get an IP at all.

I've tried taking eth0 down and bringing it up.
I've tried running sudo dhclient eth0, it never gets a response to DHCPDISCOVER
I've done a lot of googling, but no one seems to have run into my specific issue.

Any ideas? Output of a few commands below:

```
abrown@sea-abrown:~$ dmesg | grep eth
[    2.611502] 0000:02:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:16:41:ac:f0:ef
[    2.611506] 0000:02:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.611583] 0000:02:00.0: eth0: MAC: 2, PHY: 2, PBA No: 005301-003
[    3.973260] Driver 'sd' needs updating - please use bus_type methods
[    4.161535] Driver 'sr' needs updating - please use bus_type methods
[   36.466999] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.042578] 0000:02:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   38.042585] 0000:02:00.0: eth0: 10/100 speed: disabling TSO
[   38.043890] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   38.044621] bridge-eth0: up
[   38.044628] bridge-eth0: attached
[   48.836065] eth0: no IPv6 routers present
abrown@sea-abrown:~$ 
abrown@sea-abrown:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:16:41:ac:f0:ef
Sending on   LPF/eth0/00:16:41:ac:f0:ef
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
abrown@sea-abrown:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:41:ac:f0:ef  
          inet6 addr: fe80::216:41ff:feac:f0ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:4141 (4.1 KB)  TX bytes:3442 (3.4 KB)
          Memory:ee000000-ee020000 

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

pan0      Link encap:Ethernet  HWaddr 46:ed:d8:9d:ee:b9  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.109.1  Bcast:172.16.109.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.199.1  Bcast:192.168.199.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:03:c9:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-03-C9-2C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

abrown@sea-abrown:~$ 




```

---

### Post by thewise1 on 2009-02-11
Any ideas?

---

### Post by Iowan on 2009-02-11
Usually more of a wireless issue, but you might see if **acpi** is causing issues by turning it off. Though it didn't solve his problem, [this]("http://ubuntuforums.org/showthread.php?t=1065414") post has details.  I should also mention that I have no experience with **vmware**.

---

### Post by odium1 on 2009-02-11
post the results of:

```
lspci
```

and

```
uname -a
```

i don't have much experience with vmware either. but trial and error usually lead to the right path :)

---

### Post by thewise1 on 2009-02-12
> **odium1 said:**
> post the results of:

```
lspci
```

and

```
uname -a
```

i don't have much experience with vmware either. but trial and error usually lead to the right path :)
```
abrown@sea-abrown:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
abrown@sea-abrown:~$ 

```

and uname-a:

```
abrown@sea-abrown:~$ uname -a
Linux sea-abrown 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

```

Also, I'm reading the post about ACPI next

---

### Post by thewise1 on 2009-02-12
Ok now that I'm home I plugged it into my netgear/dd-wrt router, it worked perfectly.

Is there a form of DHCP that doesn't work with the default ubuntu settings? I'd rather not go back to work tomorrow and find out it's still not working there.

---

### Post by odium1 on 2009-02-12
hmm that's strange.. i was having that problem last week, except it was reverse.. I could connect at work but not at home. that kernel you're running has a known issue dealing with the ethernet drivers.. I had to get kernelcheck and update to the newest kernel release which is 2.6.28-4 ultimate.

---

