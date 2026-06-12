---
title: "Network card not detected"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by asma.r on 2010-07-29
Hi 
i installed ubuntu 8.04 on my DELL Pc with an integrated network card and i added two network cards DGE 530T
the problem that the system detect both extension network card and not the integrated card
the result of lspci is :

```
00:00.0 Host bridge: Intel Corporation Eaglelake DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Eaglelake PCI Express Root Port (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Eaglelake Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Eaglelake Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
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
02:00.0 Ethernet controller: Broadcom Corporation Unknown device 1692 (rev 01)
03:00.0 Ethernet controller: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) (rev 11)
03:02.0 Ethernet controller: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) (rev 11)
```

the result of ifconfig is :

```
eth0      Link encap:Ethernet  HWaddr 00:26:5a:79:ef:f4  
          inet adr:10.64.16.15  Bcast:10.64.16.255  Masque:255.255.255.0
          adr inet6: fe80::226:5aff:fe79:eff4/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:683 erreurs:0 :0 overruns:0 frame:0
          TX packets:214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:65221 (63.6 KB) Octets transmis:20487 (20.0 KB)
          Interruption:16 

eth1      Link encap:Ethernet  HWaddr 00:26:5a:79:ef:f8  
          inet adr:192.168.1.12  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::226:5aff:fe79:eff8/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:673 erreurs:0 :0 overruns:0 frame:0
          TX packets:683 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:364263 (355.7 KB) Octets transmis:135510 (132.3 KB)
          Interruption:17 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:1487 erreurs:0 :0 overruns:0 frame:0
          TX packets:1487 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:80234 (78.3 KB) Octets transmis:80234 (78.3 KB)
```

---

### Post by Joe of loath on 2010-07-29
Is there any particular reason you need 8.04? It's 2 years old now, and it might just be that it doesn't detect the card because it doesn't have a new enough kernel.

Upgrading or reinstalling with 10.04 might well fix your problem.

---

### Post by sinekonata on 2012-11-10
I don't think you can expect lspci to list your network adaptor since it's not PCI, you said it's an integrated NCI so I think that's the reason.

I know I don't find it either. But if I input slhw instead I see my (integrated)  card details.

---

### Post by wildmanne39 on 2012-11-10
Old thread closed.

---

