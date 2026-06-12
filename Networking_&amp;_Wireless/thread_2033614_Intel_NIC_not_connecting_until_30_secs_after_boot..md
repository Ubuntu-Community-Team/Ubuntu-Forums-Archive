---
title: "Intel NIC not connecting until 30 secs after boot."
date: 2012-07-26
forum: Networking &amp; Wireless
---

### Post by schuelaw on 2012-07-26
Hi,

I have some new Dell Optiplex 9010's I'm trying to set up with Ubuntu 12.04 64bit in a computer lab.  They get their ip addresses and hostnames from our dhcp server (statically assigned by MAC address).  Problem is on boot the NIC is not active, no lights.  The machines don't get their network connections until about 30 secs after boot when I see this in dmesg:


[   32.743872] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   32.743875] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   32.744075] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   43.290104] eth0: no IPv6 routers present

There are some earlier messages:

(zeus)~> dmesg | grep eth0
[    2.097937] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 18:03:73:25:4b:11
[    2.097939] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.097975] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: 1011FF-0FF
[    3.960645] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.653405] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.653572] ADDRCONF(NETDEV_UP): eth0: link is not ready

I've installed the latest e1000e driver but the behavior is the same.  Lightdm has real issues if the network isn't up (this may be because in my network it authenticates users via a kerberos server which it can't reach).  Also, lightdm doesn't recover when the network does become available, I have to manually restart it once the network appears in order for it to work.

An interesting side note: I booted one of the other dell 9010's that still has windows 7 on it from the factory.  During that boot, the NIC lights come on and stay on very early in the boot process.  This makes me suspect kernel parameters.

Finally, here's lspci:
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)

(there's also the wake on lan issue, but that's for another day)

Any help?

Thanks,
Albert

---

### Post by schuelaw on 2012-07-26
As a follow up, I'm working on this machine in my office on a little Netgear 5 Port Gbit switch.  When I bypass the switch and go directly into the wall port, the NIC wakes up much sooner in the boot process.  Not early enough to help, but significantly earlier.

---

### Post by edwtests on 2012-08-01
I have exactly the same problem on a new installation of 12.04LTS Server 64bit on VMWare ESXi 5.

lspci shows: 
```
02:00.0 Ethernet controller: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) (rev 01)
```and dmesg shows the following. Note the time difference. Probably caused by the DHCP client trying to resolve on a dead link: 
```

[    2.249134] sd 2:0:0:0: [sda] Attached SCSI disk
[    5.804860] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[   32.378538] ADDRCONF(NETDEV_UP): eth0: link is not ready

``` ...
```

[   32.456221] piix4_smbus 0000:00:07.3: Host SMBus controller not enabled!
[   32.457236] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.461774] [480]: VMCI: shared components initialized.
[   32.461789] Probing for vmci/PCI.
[   32.461819] vmci 0000:00:07.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   32.461848] Found vmci/PCI at 0x1080, irq 16.
[   32.461875] VMCI: using capabilities 0x4.
[   32.461911] [480]: VMCI: Host capability check: PASSED.
[   32.461946] Registered vmci device.

```...
```

[   32.632844] type=1400 audit(1343805972.821:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=547 comm="apparmor_parser"
[   32.633087] type=1400 audit(1343805972.821:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=547 comm="apparmor_parser"
[   32.633226] type=1400 audit(1343805972.821:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=547 comm="apparmor_parser"
[   32.633966] type=1400 audit(1343805972.821:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=581 comm="apparmor_parser"
[   32.634230] type=1400 audit(1343805972.825:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=581 comm="apparmor_parser"
[   32.634370] type=1400 audit(1343805972.825:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=581 comm="apparmor_parser"
[   32.635678] type=1400 audit(1343805972.825:8): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=585 comm="apparmor_parser"
[   32.637042] type=1400 audit(1343805972.825:9): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=586 comm="apparmor_parser"

```...
```

[   32.694130] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   32.694685] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   32.695628] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```This boot order causes a 30 second delay. :(

---

### Post by Kirk Schnable on 2012-08-01
This sounds like Spanning Tree Protocol to me.  But I don't think that little 5 port switch would have spanning tree.  You can check and see if it does by plugging 2 ports into each other with 1 cable.  If the connection doesn't establish, the switch has spanning tree.  If there's a packet storm, there's no spanning tree.

Spanning Tree typically does cause a long delay in the network coming up, because it has to listen on the port for awhile and make sure you're a client, not a loop.

Kirk

---

### Post by edwtests on 2012-08-01
I don't think it's hardware related since it happens to both of us at different locations; and I also have other virtual machines (ubuntu 12.04lts but upgraded from 10.10) with static IPs that boot up just fine.

I suspect the 30 seconds come from trying to get an IP before the PCI cards have been setup. DHCP timeout?

Something needs to be done to setup the adapters before trying to use them, but I don't dare to edit the init scripts myself.

---

### Post by Grenage on 2012-08-01
> **Kirk Schnable said:**
> This sounds like Spanning Tree Protocol to me.  But I don't think that little 5 port switch would have spanning tree.  You can check and see if it does by plugging 2 ports into each other with 1 cable.  If the connection doesn't establish, the switch has spanning tree.  If there's a packet storm, there's no spanning tree.

Spanning Tree typically does cause a long delay in the network coming up, because it has to listen on the port for awhile and make sure you're a client, not a loop.

That would also have been one of the first things I'd have checked, if not for this:

> **schuelaw said:**
> An interesting side note: I booted one of the other dell 9010's that still has windows 7 on it from the factory.  During that boot, the NIC lights come on and stay on very early in the boot process.  This makes me suspect kernel parameters.

---

