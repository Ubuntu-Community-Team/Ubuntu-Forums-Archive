---
title: "Lucid: network issues with 2.6.32"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by raoul29 on 2010-05-24
Hi,

I upgraded from 9.10 to 10.04 and my network worked fine at the beginning. Then it stopped working with the network manager showing 'No network connection'. I didn't change any conf, just installed the new updates that I was given.

Using kernel 2.6.32-22 I cannot get the network to work at all. I get:

rgr@iker:~$ sudo mii-tool 
eth0: no link
eth1: no link

Although when boot from the CD (with another linux distribution), the network works fine, so I guess it cannot be a hardware/router issue.

When booting using kernel 2.6.31-21, the network manager still shows 'No network connections' but mii-tool says:

rgr@iker:~$ sudo mii-tool 
eth0: negotiated 100baseTx-FD flow-control, link ok
eth1: no link

and the ifconfig output is:

rgr@iker:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:04:7e:06  
          inet6 addr: fe80::4261:86ff:fe04:7e06/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:320 (320.0 B)  TX bytes:810 (810.0 B)
          Interrupt:36 Base address:0x6000 

In this case, when running dhclient manually, the network works again:

rgr@iker:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/40:61:86:04:7e:06
Sending on   LPF/eth0/40:61:86:04:7e:06
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.34 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.34 from 192.168.1.1
bound to 192.168.1.34 -- renewal in 41884 seconds.

Also the related dmesg output is:

[    3.563779] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.563795] r8169 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.563834] r8169 0000:03:00.0: setting latency timer to 64
[    3.563873]   alloc irq_desc for 36 on node 0
[    3.563874]   alloc kstat_irqs on node 0
[    3.563886] r8169 0000:03:00.0: irq 36 for MSI/MSI-X
[    3.564254] eth0: RTL8168d/8111d at 0xffffc90000666000, 40:61:86:04:7e:06, XID 281000c0 IRQ 36
[    3.568568] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.568582] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.568612] r8169 0000:04:00.0: setting latency timer to 64
[    3.568651]   alloc irq_desc for 37 on node 0
[    3.568652]   alloc kstat_irqs on node 0
[    3.568663] r8169 0000:04:00.0: irq 37 for MSI/MSI-X
[    3.569042] eth1: RTL8168d/8111d at 0xffffc90000650000, 40:61:86:04:7e:07, XID 281000c0 IRQ 37

and

[   15.813721] r8169: eth0: link down
[   15.813865] type=1505 audit(1274728155.108:6): operation="profile_replace" pid=3331 name=/sbin/dhclient3
[   15.814116] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.814351] type=1505 audit(1274728155.108:7): operation="profile_replace" pid=3331 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   15.814592] type=1505 audit(1274728155.108:8): operation="profile_replace" pid=3331 name=/usr/lib/connman/scripts/dhclient-script
[   15.814790] r8169: eth1: link down
[   15.815080] ADDRCONF(NETDEV_UP): eth1: link is not ready


Any ideas? Not sure what else to look for? How can I have an eth link with 2.6.31 but not with 2.6.32 ??

Regards,

Raoul.

---

### Post by talz13 on 2010-05-24
I believe I'm having the exact same problem here!  On the plus side, I found one of my spare NICs... it was in the PC that's having this problem, and I thought it was odd that there were both eth0 and eth1 listed!


Network issues are the worst to troubleshoot, you have to sit at the affected computer, and you can't even browse for help from there while trying to fix it!

Subscribing for updates...

---

### Post by raoul29 on 2010-05-25
Talz13, do you also have a r8169?

Still haven't figured out why it isn't working under 2.6.32, although with 2.6.31 network-manager now works correctly after I disabled IPv6 in its conf.

---

### Post by bernddude on 2010-05-25
Hi Raoul, you just gave me an idea for my wifi issues , disable ip6 ? how did you do this in lucid lynx ? could you give me a pointer , thx bernd

---

### Post by talz13 on 2010-05-25
> **raoul29 said:**
> Talz13, do you also have a r8169?

Still haven't figured out why it isn't working under 2.6.32, although with 2.6.31 network-manager now works correctly after I disabled IPv6 in its conf.

I believe that it is using either the r8168 or r8169 module...  I just checked my server (both PCs in this case are using Gigabyte mobo) and its network is listed as:```
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:d0:27:53:6d
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=0 link=yes module=r8169 multicast=yes port=MII speed=1GB/s
```
My server is running ubuntu 9.04 and has no current issues.

---

### Post by dillzz on 2010-05-25
Raoul,

I am having issues as well.  Check this  thread
[http://ubuntuforums.org/showthread.php?t=1022411&highlight=realtek](http://ubuntuforums.org/showthread.php?t=1022411&highlight=realtek)

I tried this in /etc/rc.local:
/etc/init.d/networking stop && /etc/init.d/networking start

-Dillzz

---

### Post by raoul29 on 2010-05-25
To disable IPv6, right click on the network-manager icon - Choose the connection - Edit - IPv6 settings - choose ignore.

---

### Post by talz13 on 2010-05-25
I just rebooted using 2.6.32-21 (instead of -22, it's all I have since it was a clean install of 10.04), and sudo mii-tool shows:```
eth0: negotiated 1000baseT-HD flow-control, link ok
eth1: no link
```but I still can't get connected by doing anything that I can think of (sudo /etc/init.d/networking stop, start, etc....)

And yes, it is using the r8169 driver for my RTL8111/8168B PCI Express Gigabit Ethernet Controller, version 2.3LK-NAPI on the PC that I'm having problems with.

---

### Post by Erhnam on 2010-06-27
Same problem here!

---

