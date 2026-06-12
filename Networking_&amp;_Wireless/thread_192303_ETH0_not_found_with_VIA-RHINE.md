---
title: "ETH0 not found with VIA-RHINE"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by jc_linux on 2006-06-08
Hello, 
   I exuse for my not very academic English. Not finding a response to my problem on the French forums, I try to widen the number of expert.

   Under Windows, my system goes correctly (computer connected to a router). Under Ubuntu, plus nothing does not function. The network (eth0) is not even present any more.

   I copy the traces carried out on my PC transmits to you by hoping that that will enable you to help me to advance on this subject.

   Thank you in advance of your assistance

```

**sudo modprobe -r via-rhine && sudo modprobe via-rhine**
    No msg

**dmesg**
[4294860.019000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294860.019000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 217
[4294860.019000] Invalid MAC address
[4294860.019000] via-rhine: probe of 0000:00:12.0 failed with error -5

**ifconfig -a**
lo        Lien encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:HÃ´te
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reÃ§us:5 erreurs:0 :0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reÃ§us:272 (272.0 b) Octets transmis:272 (272.0 b)

sit0      Lien encap:IPv6-dans-IPv4
          NOARP  MTU:1480  Metric:1
          Packets reÃ§us:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reÃ§us:0 (0.0 b) Octets transmis:0 (0.0 b)

**lspci**
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)

**cat /etc/network/interfaces**
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

**lsmod**
Module                  Size  Used by
via_rhine              23940  0
mii                     5888  1 via_rhine

```

---

### Post by jhenager on 2007-02-03
I get the same response from dmesg:
[17182020.940000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker

but lspci doesn't find the via.

In the meantime, i used a 3Com 97TX card, and that has been working fine for a few months.
If you still haven't resolved this, I'd suggest getting an external card, preferably from a well known vendor.
I learned a few years ago that linux in general doesn't always find or use the embedded, cheaper LAN cards on motherboards.

---

### Post by Tyreal on 2008-01-23
Hate to bump up something this old but I seem to be having the same issue and can't really find any solid explanation google or otherwise.  So here's the full scenario:

I have a 3com card in one of my fileservers:

```
3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
```

This was giving me lots of errors such as:

```
[66135.320734] eth0: Transmit error, Tx status register 82.
```

After unsuccessfully battling with this little beast, I figured I'd try another card.  Come to find out this one is a bigger piece of work.  So I'm running 2.6.20-16-server as the kernel (wanted to make sure I had the latest version), current distro release is:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"
```

The card is a Dlink DFE-530TX+, which registers in lspci as:
```

02:08.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)
```

So, I have both cards in the system, and upon rebooting, I get this:

```
[   33.428655] eth1: VIA Rhine III at 0x1dc00, 00:17:9a:bc:68:4f, IRQ 20.
[   33.429382] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   37.448470] eth0:  setting half-duplex.
[   49.322238] eth0: no IPv6 routers present
```

okay, everything looking good so far, eth0 for the 3com, eth1 for the dlink, and just to make sure the driver isn't at fault:

```
# dmesg | grep via
[   32.036972] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
```

Driver loads just fine, now ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:04:76:E7:CF:D4
          inet addr:[removed]  Bcast:[removed]  Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fee7:cfd4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:724 errors:0 dropped:0 overruns:1 frame:0
          TX packets:359 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:57992 (56.6 KiB)  TX bytes:38303 (37.4 KiB)
          Interrupt:18 Base address:0x8800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

no eth1 at all... and just to be sure:

```
# lsmod | egrep "(via|3c59x)"
via_rhine              25864  0
3c59x                  46760  0
mii                     6656  2 via_rhine,3c59x
```

both modules show up and are linked to the mii module.  If anyone else has any ideas I'm all open, this has me completely stumped.

---

