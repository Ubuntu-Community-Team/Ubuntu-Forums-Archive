---
title: "On Board Intel 82540EM Wired NIC Not Connecting to Network"
date: 2009-06-28
forum: Networking &amp; Wireless
---

### Post by Netzilla on 2009-06-28
This is a wired connection using the above integrated NIC.  It is on a dual-boot system, one partition Windows and the other Ubuntu 9.04.  The Windows partition can connect to the network with no problems but Ubuntu cannot.  Ubuntu was able to connect as of last night but when I booted up the PC this morning it no longer worked.

Here's some of the testing I've already done:

more /proc/version
```

Linux version 2.6.28-13-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #44-Ubuntu SMP Tue Jun 2 07:57:31 UTC 2009

```

libpci -v

```

01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
	Subsystem: Intel Corporation 82540EM Gigabit Ethernet Controller
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fe9e0000 (64-bit, non-prefetchable) [size=128K]
	Memory at fe9d0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at df40 [size=64]
	Expansion ROM at 40000000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: e1000
	Kernel modules: e1000

```

sudo lshw -C network
```

  *-network DISABLED      
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A latency=64 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ae:c8:f0:fe:f1:be
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

ifconfig
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:298 errors:0 dropped:0 overruns:0 frame:0
          TX packets:298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17645 (17.6 KB)  TX bytes:17645 (17.6 KB)

```

ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:316 errors:0 dropped:0 overruns:0 frame:0
          TX packets:316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18641 (18.6 KB)  TX bytes:18641 (18.6 KB)

pan0      Link encap:Ethernet  HWaddr 32:9a:d2:3a:4a:bf  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


sudo ifdown eth0
```

ifdown: interface eth0 not configured

```

sudo ifup eth0
```

SIOCSIFHWADDR: Cannot assign requested address
Failed to bring up eth0.

```

Contents of /etc/network/interfaces
```

auto eth0
iface eth0 inet dhcp
pre-up ifconfig eth0 hw ether 00:00:00:00:00:00
auto lo
iface lo inet loopback

```

I've also attached the results of dmesg (in dmesg.doc).

Does anyone know what may be happening or anything else I can try?

Thanks in advance.

Deric

---

### Post by Netzilla on 2009-06-29
bump

---

### Post by chili555 on 2009-06-29
> auto eth0
iface eth0 inet dhcp
[COLOR="Red"]pre-up ifconfig eth0 hw ether 00:00:00:00:00:00[/COLOR]
auto lo
iface lo inet loopbackWhy is the MAC address being changed?

Also, I note this in your *dmesg*:> e1000: 0000:01:0c.0: e1000_probe: The EEPROM Checksum Is Not ValidA google search of 'e1000 bad checksum' yields some scary stuff.

I think I would remove the pre-up above and reboot. Run *dmesg* again and see if there is any improvement.

---

### Post by Netzilla on 2009-06-29
Thanks for the response,

> **chili555 said:**
> Why is the MAC address being changed?

That was from another website I'd checked while troubleshooting this problem myself.  Obviously, the change didn't help.  I've gone ahead and removed it and rebooted.

> Also, I note this in your *dmesg*:A google search of 'e1000 bad checksum' yields some scary stuff.

I'll have to do some checking on that front myself.  I wonder if I need to download the module and compile it myself.  Unfortunately, I don't know what I'd have to do to remove the faulty e1000 module first.

> I think I would remove the pre-up above and reboot. Run *dmesg* again and see if there is any improvement.

I did that and ran the same tests as shown in my first message.  The results were the same with these two exceptions:

sudo ifdown eth0
```

RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 3563
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:00:00:00:00:00
Sending on   LPF/eth0/00:00:00:00:00:00
Sending on   Socket/fallback

```

sudo ifup eth0
```

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFFLAGS: Cannot assign requested address
SIOCSIFFLAGS: Cannot assign requested address
Listening on LPF/eth0/00:00:00:00:00:00
Sending on   LPF/eth0/00:00:00:00:00:00
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
RTNETLINK answers: Network is down
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2

```

As far as dmesg goes, I noted the following in the results:
```

[    7.211633] Intel(R) PRO/1000 Network Driver - version 7.3.21-k3-NAPI
[    7.211638] Copyright (c) 1999-2006 Intel Corporation.
[    7.211704] e1000 0000:01:0c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.448738] e1000: 0000:01:0c.0: e1000_probe: The EEPROM Checksum Is Not Valid
[    7.661378] /*********************/
[    7.661381] Current EEPROM Checksum : 0xbfff
[    7.661383] Calculated              : 0x1852
[    7.661385] Offset    Values
[    7.661387] ========  ======
[    7.661391] 00000000: c0 82 66 a6 01 80 0a 84 ff bf ff bf ff bf ff bf 
[    7.661394] 00000010: c1 b8 32 83 ff bf ff bf 7b 80 ff bf ff bf ff bf 
[    7.661397] 00000020: ff bf ff bf ff bf ff bf ff bf ff bf ff bf ff bf 
[    7.661400] 00000030: ff bf ff bf ff bf ff bf ff bf ff bf ff bf ff bf 
[    7.661403] 00000040: ff bf ff bf ff bf ff bf ff b8 00 80 ff bf ff bf 
[    7.661405] 00000050: ff bf ff bf ff bf ff bf ff bf ff bf ff bf ff bf 
[    7.661408] 00000060: ff bf ff bf ff bf ff bf ff bf ff bf ff bf ff bf 
[    7.661411] 00000070: ff bf ff bf ff bf ff bf ff bf ff bf ff bf ff bf 
[    7.661416] Include this output when contacting your support provider.
[    7.661419] This is not a software error! Something bad happened to your hardware or
[    7.661422] EEPROM image. Ignoring this problem could result in further problems,
[    7.661426] possibly loss of data, corruption or system hangs!
[    7.661429] The MAC Address will be reset to 00:00:00:00:00:00, which is invalid
[    7.661432] and requires you to set the proper MAC address manually before continuing
[    7.661434] to enable this network device.
[    7.661437] Please inspect the EEPROM dump and report the issue to your hardware vendor
[    7.661440] or Intel Customer Support.
[    7.661442] /*********************/
[    7.661444] e1000: 0000:01:0c.0: e1000_probe: Invalid MAC Address
[    7.664777] e1000: 0000:01:0c.0: e1000_probe: (PCI:33MHz:32-bit) 00:00:00:00:00:00
[    8.101917] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection

```

So it looks like I'm still getting the 'bad checksum'.  I've attached the full dmesg results just in case there's anything else useful in there.

---

### Post by Netzilla on 2009-06-29
Huh.  I fixed it.  I did a bit more googling specifically for the "e1000_probe: The EEPROM Checksum Is Not Valid" error (thanks chili555 for pointing that out to me) and came across a reference to fixing this type of thing simply by updating the BIOS.

So, I grabbed a BIOS update.  Fortunately, I'm on a dual-boot system as the one offered by DELL is only for Windows.  Now everything works!

It's always the simple stuff (like keeping your BIOS up to date) that get's ya.

---

### Post by chili555 on 2009-06-30
Outstanding! Glad it's working now!

---

