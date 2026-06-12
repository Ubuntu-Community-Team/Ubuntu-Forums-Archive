---
title: "Wired network not working"
date: 2012-10-29
forum: Networking &amp; Wireless
---

### Post by brucardoso2 on 2012-10-29
As old times guys :popcorn:
I can't figure out why my network interface doesn't appear, I'm on Ubuntu 10.10

Here are some dumps to get you guys going, ask if you need anything else:
```

**lspci**
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 0e)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 05)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 05)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 05)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 05)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 05)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d5)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 05)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)

```

```

**cat /etc/network/interfaces **
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

```

**cat /etc/NetworkManager/nm-system-settings.conf **
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```

```

**ifconfig -a**
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

```
```

**sudo lshw -C Network**
(nothing)

```

---

### Post by sonicb00m on 2012-10-31
I also have a problem with the wired network. When I start up the computer the network in unreachable and the network icon shows and empty shell or whatever the hell it is supposed to be.

If i keep toggling to the enable/disable network eventually it works and I can use the network as normal.

This problem appeared one day after recent updates to 12.04 and has carried over to 12.10 when I did an upgrade without freshly installing.

---

### Post by brucardoso2 on 2012-11-28
Can anyone help us?

---

