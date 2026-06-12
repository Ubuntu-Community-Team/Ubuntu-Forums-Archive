---
title: "Wireless suddenly stopped working"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by Gustav on 2009-05-14
I have a Acer Aspire One and wireless have always worked for me before, but this morning it failed to log on to the wireless network (it acted as if i had the wrong password). I rebooted the computer and then it acted as if I had no wifi on the computer at all.

Output from ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:23:8b:36:f6:5d  
          inet addr:85.229.139.13  Bcast:85.229.143.255  Mask:255.255.240.0
          inet6 addr: fe80::223:8bff:fe36:f65d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:649200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:273794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:848482086 (848.4 MB)  TX bytes:165548024 (165.5 MB)
          Interrupt:252 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8300 (8.3 KB)  TX bytes:8300 (8.3 KB)

```
Output from lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

I've been using the ath5k drivers and they have a line in /etc/modules

PS I'm using Jaunty

---

### Post by Peter09 on 2009-05-14
Check that you have not switched the wireless off with the small rocker switch.

If not can you post the output of

```
lshw -C network
```

---

### Post by Gustav on 2009-05-14
I've tried switching it on and off many times ;)

```
gustav@LillaRosa:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:36:f6:5d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=85.229.139.13 latency=0 module=r8169 multicast=yes
```

---

### Post by Gustav on 2009-05-14
When using sudo:```
gustav@LillaRosa:~$ sudo lshw -C network
[sudo] password for gustav: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:36:f6:5d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=85.229.139.13 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
```

---

### Post by Peter09 on 2009-05-14
This looks horribly like a hardware fault - I cannot see any wireless device here at all.

---

### Post by Peter09 on 2009-05-14
Does
```
dmesg | more
```

show any errors?

---

### Post by Gustav on 2009-05-14
> **Peter09 said:**
> Does
```
dmesg | more
```

show any errors?
Just some ACPI errors caused by AE_ALREADY_EXISTS error and some "[drm:i915_setparam] *ERROR* unknown parameter 4"

---

### Post by Peter09 on 2009-05-14
Had a quick google and some of these errors _*may*_ be to do with BIOS configurations. It may be worth looking around the BIOS of your machine to see if the internal wireless card has been disabled from within the BIOS.

---

### Post by Gustav on 2009-05-14
I'll give it a try

---

### Post by Gustav on 2009-05-14
Nah, definetly a software problem. Works on live-usb.

---

### Post by Gustav on 2009-05-14
OK, now it works again (without me doing anything :P)

Thank you for the help!

---

