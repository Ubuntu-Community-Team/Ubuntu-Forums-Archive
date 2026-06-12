---
title: "eth0 not showing upon ifconfig!!"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by balteo on 2009-11-12
Hello,
I've just installed Jaunty on a very recent computer and my network adapter does not appear as eth0.

-Here is the output of ifconfig
```

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:4 erreurs:0 :0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:240 (240.0 B) Octets transmis:240 (240.0 B)

```-However lspci shows my network adapter (see towards the end of the output).
```

00:00.0 Host bridge: Intel Corporation Clarksfield/Lynnfield DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Clarksfield/Lynnfield PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Clarksfield/Lynnfield System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Clarksfield/Lynnfield Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Clarksfield/Lynnfield System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Clarksfield/Lynnfield Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation Ibex Peak USB2 Enhanced Host Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Ibex Peak PCI Express Root Port 1 (rev 05)
00:1c.3 PCI bridge: Intel Corporation Ibex Peak PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation Ibex Peak USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Ibex Peak LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation Ibex Peak 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Ibex Peak SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0659 (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation Device 1692 (rev 01)
03:00.0 PCI bridge: Creative Labs Device 7006
04:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG

```Here is the std error from a networking restart.
```

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device

```and std output from the same restart:
```

 * Reconfiguring network interfaces...
Failed to bring up eth0.
   ...done.

```Note that I have added eth0 in /etc/network/interfaces.

Can anyone help?

Thanks,

Julien.

---

### Post by Iowan on 2009-11-12
Check **lshw -C network** and **ifconfig -a** (the option should show interfaces, even if they aren't up/active).

---

### Post by balteo on 2009-11-12
I finally downloaded the driver and installed it and it now works!
Thanks for the tip though.
J.

---

