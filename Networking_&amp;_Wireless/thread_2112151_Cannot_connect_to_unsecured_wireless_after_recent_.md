---
title: "Cannot connect to unsecured wireless after recent updates"
date: 2013-02-03
forum: Networking &amp; Wireless
---

### Post by Akhety on 2013-02-03
After doing some updates almost a week ago, my laptop will not connect to the unsecured wireless on campus, although it will connect to my secured network at home. However, this is my work laptop, and it really needs to be able to connect to the campus wireless.

I have wicd, and it continually gets stuck on "obtaining ip address." I've tried doing it manually by typing into terminal:

```
sudo iwconfig eth1 essid "uchicago" 
dhclient
```

iwconfig shows the correct essid, but I have no connectivity. I see this: (typing on my ipad, sorry)

```
eth1 IEEE 802.11abg ESID: uchicago
Mode: Managed Frequency:2.462 Ghz Access Point: Not-Associated
Retry: long limit: 7 RTS thr:off Fragment thr: off
Power Management:off
```

I would appreciate any and all advice on what to try. I've been trying for days to try to get this to work, and nothing works. Please type in full commands when replying. I'm not a complete beginner, but nearly so.

---

### Post by ahallubuntu on 2013-02-04
~

---

### Post by Akhety on 2013-02-04
I am unfortunately transcribing this from my ipad.

I am using 12.04 and I did both update and upgrade.

I think this is the relevant line:

```
03.00.0 Network Controller: Broadcom Corporation BCM4312 802,11b/g LP-PHY (rev 01)
04.00.0 Ethernet Controller: Realtek Semiconductor Co., Ltd. RTL8101E/RL8102E PCI Express Fast Ethernet controller (rev 02)
```

Please let me know if there is something else you need. I wish I could just copy and paste.

---

### Post by ahallubuntu on 2013-02-04
~

---

### Post by Akhety on 2013-02-07
I have some new information on my issue, though no fixes yet, so I thought I'd post here.

I updated my Broadcom driver, I still had the same issue: I could connect to my home wireless network, but not the one on campus. I took it the campus IT help desk, but they don't officially support Ubuntu, so the guy there knew about as much as I did about trying to fix it.

I have been able to connect sometimes, but not always. I am now able to connect to the on-campus wireless if I create a network first. Then, try to connect to the unsecured wireless and it will connect and then give me an internal error message. But it leaves me connected. 

I can't figure out how to copy the internal error message, and I can't find any documentation online on how to do this, otherwise I'd post it here. 

But I can post this:

```
sudo lshw -C network
[sudo] password for kara: 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:23:08:1c:f6:f4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=128.135.196.39 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:cc:44:26
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:2000(size=256) memory:f0610000-f0610fff memory:f0600000-f060ffff memory:f0620000-f063ffff

```

and this:

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
02:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
02:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

If that is helpful for anyone, I'd appreciate any kind of advice or suggestions now that I can actually connect (sometimes, when my computer feels like it). 

The internal error's title is: NetworkManager crashed with SIGSEGV in dbus_g_proxy_begin_call()

---

