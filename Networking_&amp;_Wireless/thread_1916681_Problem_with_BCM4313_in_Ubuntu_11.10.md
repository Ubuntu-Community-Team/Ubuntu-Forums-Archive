---
title: "Problem with BCM4313 in Ubuntu 11.10"
date: 2012-01-28
forum: Networking &amp; Wireless
---

### Post by optima4 on 2012-01-28
I've been searching around this forum for months and months and months now. Still 11.10 is horrible with WiFi connection. Horrible is putting it nicely. I dual-booted an earlier version (Maverick), which is running beautifully. I am going to just erase Oneiric altogether, but I have to either wait for my external HDD to get here or I have to transfer all the files myself from the dul-booted, which I do not know how to do yet. 

Couldn't there be a quick fix to the WiFi connection in 11.10 for now, or least something I can work at?

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr b8:70:f4:73:9e:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

eth1      Link encap:Ethernet  HWaddr 90:00:4e:97:25:3a  
          inet addr:192.168.2.9  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::9200:4eff:fe97:253a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:288270 errors:0 dropped:0 overruns:0 frame:1337551
          TX packets:175826 errors:17 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:414833617 (414.8 MB)  TX bytes:16499486 (16.4 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6152 (6.1 KB)  TX bytes:6152 (6.1 KB)

```

lspci

```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
```

lspci -v
```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at 98180000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 60c0 [size=8]
    Memory at 80000000 (32-bit, prefetchable) [size=256M]
    Memory at 98000000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, fast devsel, latency 0
    Memory at 98100000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at 98200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: 97000000-97ffffff
    Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 96000000-96ffffff
    Prefetchable memory behind bridge: 0000000091000000-0000000091ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 6080 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 6060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 6040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at 6020 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, medium devsel, latency 0, IRQ 22
    Memory at 98204400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
    I/O ports at 60b8 [size=8]
    I/O ports at 60cc [size=4]
    I/O ports at 60b0 [size=8]
    I/O ports at 60c8 [size=4]
    I/O ports at 60a0 [size=16]
    Memory at 98204000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: medium devsel, IRQ 10
    I/O ports at 6000 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at 97000000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 5000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Broadcom Corporation Device 0510
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at 96000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, bcma, brcmsmac

```



 :mad:

Whats up with this? I can't get ANYTHING done!

I constantly have this happening in the attachment. It is on 3 tabs right now and I could not even add the attachment without a ridiculous amount of loading time. I can't load any of the pages and I can't even turn in my homework because of this. 

I would switch the other Maverick and easily use the Internet, but I have to use this one to complete my homework assignment.

---

### Post by carl4926 on 2012-01-28
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

Your broadcom wireless is probably the worst there is in broadcom

---

### Post by ts3 on 2012-01-28
The b43 drivers do not support BCM4313 unfortunately.  You need the get the bcmwl-kernel-source driver from the software centre.  You also need to uninstall any b43 drivers and de-activate the STA proprietary drivers, if activated

If the wireless is still not working you need to check for conflicts and blacklisted drivers.  The broadcom website is a good starting point, check out the readme.txt, especially the part called Fresh Installation.  

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

You don't actually need to build the driver from the broadcom website as long as you have wired access you can install it from the software centre.

Cheers :)

**CORRECTION:**

Ooops, sorry, I take the above back, after I looked at the info you posted more carefully: you seem to be loading the right driver, wl.  No idea what's causing the slow connection then, sorry :)

---

### Post by coffeecat on 2012-01-28
@optima4, the BCM4313 in my HP netbook works well and out-of-the-box in 11.10 with the default open-source driver. Did you upgrade to Oneiric from an earlier version or did you do a fresh install? And did you try to install either the STA or b43 driver?

---

### Post by optima4 on 2012-01-28
I have this wireless adapter connected to the computer. It is a netbook. Does not even work with 11.10. Works fine on the other. 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045](http://www.newegg.com/Product/Product.aspx?Item=N82E16833704045)


Its a fresh install of 11.10

The broadcom wireless card works flawlessly with 10.10 on the dual-boot.

Its just not working with 11.10. I'm just copying the files over and scrapping it.

---

### Post by kevdog on 2012-01-28
Yes before you scrap it you could help us by doing the following:

Seeing what driver your card is being assigned in 10.10 and 11.10.  I want to see if there is a difference.  There should be no reason for you to scrap the 11.10 build just because a single driver isn't working out of the box.  With just a little work I am fairly certain you can have the same driver working.

---

### Post by optima4 on 2012-01-29
Sure I will get that stuff for you. 

I was thinking of overwriting it with LMDE. I'm now using LMDE and it isn't much better than 11.10. So, I'm still considering what to do. Is it possible to do a hardware upgrade on my wireless card for this LT27 Gateway Netbook?

---

### Post by bkratz on 2012-01-29
> **optima4 said:**
> Sure I will get that stuff for you. 

I was thinking of overwriting it with LMDE. I'm now using LMDE and it isn't much better than 11.10. So, I'm still considering what to do. Is it possible to do a hardware upgrade on my wireless card for this LT27 Gateway Netbook?

since the original post shows so many framing errors, 

 RX packets:288270 errors:0 dropped:0 overruns:0 [COLOR="Red"]frame:1337551[/COLOR]

it may be worth the time to investigate the MTU setting:

[http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html](http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html)


As a temporary test you could simply 

```
sudo ifconfig eth1 mtu 1492
```


and see if the speed improves. Should cause less errors.

---

