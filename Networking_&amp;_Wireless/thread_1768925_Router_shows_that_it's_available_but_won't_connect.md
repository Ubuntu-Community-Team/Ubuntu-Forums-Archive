---
title: "Router shows that it's available but won't connect"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by alaaji on 2011-05-27
I just installed Ubuntu 11.04 on an old Toshiba Satellite A20 for my kids.  I attempted to connect through the router but I can't get it to work.  Even manually creating a new connection does nothing.

carlos@carlos-Satellite-A20:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:39:39:d1:d7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xed00 

eth1      Link encap:Ethernet  HWaddr 00:02:2d:7e:0a:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

carlos@carlos-Satellite-A20:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

As you can see nothing is available at all.

---

### Post by josephmills on 2011-05-27
hi there could we please see a ```
lspci -nn
``` and a ```
rfkill list all 
``` thanks

---

### Post by alaaji on 2011-05-28
As requested:

```
carlos@carlos-Satellite-A20:~$ lspci -nn
00:00.0 Host bridge [0600]: ALi Corporation M1672 Northbridge [CyberALADDiN-P4] [10b9:1672]
00:01.0 PCI bridge [0604]: ALi Corporation PCI to AGP Controller [10b9:5247]
00:04.0 IDE interface [0101]: ALi Corporation M5229 IDE [10b9:5229] (rev c4)
00:06.0 Multimedia audio controller [0401]: ALi Corporation M5451 PCI AC-Link Controller Audio Device [10b9:5451] (rev 02)
00:07.0 ISA bridge [0601]: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+] [10b9:1533]
00:08.0 Bridge [0680]: ALi Corporation M7101 Power Management Controller [PMU] [10b9:7101]
00:09.0 Modem [0703]: ALi Corporation M5457 AC'97 Modem Controller [10b9:5457]
00:0a.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
00:0c.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
00:0c.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
00:0c.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 04)
00:10.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 01)
00:11.0 CardBus bridge [0607]: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support [1179:0617] (rev 33)
00:12.0 System peripheral [0880]: Toshiba America Info Systems SD TypA Controller [1179:0805] (rev 05)
01:00.0 VGA compatible controller [0300]: Trident Microsystems CyberBlade XPAi1 [1023:8820] (rev 82)
```

```
carlos@carlos-Satellite-A20:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

---

### Post by dandnsmith on 2011-05-28
It looks as though the tosh has 2 ethernet ports, but no wireless, and neither of the ports is getting an IP address.

Given that the loop interface has an IP6 address, I note that hou loaded 11.04. This isn't the first network query showing a problem with allocating IP addresses and 11.04.

I'd suggest loading 10.04, where the networking doesn't have those sorts of problem.

---

### Post by Iowan on 2011-05-28
**sudo lshw -C network** will provide similar information.
My laptop calls it's wireless connection eth1.

---

### Post by alaaji on 2011-05-28
> **Iowan said:**
> **sudo lshw -C network** will provide similar information.
My laptop calls it's wireless connection eth1.

You're right, that's exactly what my laptop shows.  Is there any way to get it connected though?
```

carlos@carlos-Satellite-A20:~$ sudo lshw -C network
[sudo] password for carlos: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 10
       serial: 00:00:39:39:d1:d7
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:11 ioport:ed00(size=256) memory:f7efff00-f7efffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:7e:0a:78
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=2.6.38-6-generic firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b
```

---

### Post by dandnsmith on 2011-05-28
Well, that doesn't add anything, except to say that one of the eth interfaces is wireless (how confusing, after the nomenclature used on earlier releases).
You've still to get them IP addresses compatible with your router setup, and possible have to get the wireless one turned on.
I suggested , in another post, assigning IP4 addresses manually, but haven't heard yet whether this can/will work

---

### Post by Iowan on 2011-05-28
Perhaps it would be worth asking whether you're attempting to connect via wire or wireless - which kind of "new connection" did you create?

---

