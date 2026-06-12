---
title: "RTL8188CE wifi card not working properly"
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by bela83 on 2012-12-26
Hi everybody,

I bought the Shuttle XS35GTAV3
[http://www.shuttle.eu/products/slim/xs35gta-v3/specification/](http://www.shuttle.eu/products/slim/xs35gta-v3/specification/)
I made a fresh install of 12.10 64 bits.
```
papimami@XS35V3:~$ uname -a
Linux XS35V3 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:51:59 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

I am experiencing seemingly random wireless issues.
Here is the output of some commands :
```

papimami@XS35V3:~$ lspci
00:00.0 Host bridge: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour LP [Radeon HD 6430M]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Caicos HDMI Audio [Radeon HD 6400 Series]
02:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 80)
02:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 80)
02:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 80)
02:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev ff)

```
```

papimami@XS35V3:~$ lspci -v | tail -15
02:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 4012
        Flags: bus master, fast devsel, latency 0, IRQ 47
        Memory at d0200000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at d100 [size=128]
        I/O ports at d000 [size=256]
        Capabilities: <access denied>
        Kernel driver in use: jme
        Kernel modules: jme

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev ff) (prog-if ff)
        !!! Unknown header type 7f
        Kernel driver in use: rtl8192ce
        Kernel modules: rtl8192ce

```
```

papimami@XS35V3:~$ sudo lshw -C network
[sudo] password for papimami: 
  *-network               
       description: Ethernet interface
       produit: JMC250 PCI Express Gigabit Ethernet Controller
       fabriquant: JMicron Technology Corp.
       identifiant matériel: 0.5
       information bus: pci@0000:02:00.5
       nom logique: eth0
       version: 03
       numéro de série: 80:ee:73:40:89:1a
       taille: 100Mbit/s
       capacité: 1Gbit/s
       bits: 32 bits
       horloge: 33MHz
       fonctionnalités: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=full ip=192.168.1.11 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       ressources: irq:47 mémoire:d0200000-d0203fff portE/S:d100(taille=128) portE/S:d000(taille=256)
  *-generic DÉSACTIVÉ
       description: Interface réseau sans fil
       produit: Illegal Vendor ID
       fabriquant: Illegal Vendor ID
       identifiant matériel: 0
       information bus: pci@0000:03:00.0
       nom logique: wlan0
       version: ff
       numéro de série: e0:91:53:6f:b5:90
       bits: 32 bits
       horloge: 66MHz
       fonctionnalités: bus_master vga_palette cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.5.0-21-generic firmware=N/A latency=255 link=no maxlatency=255 mingnt=255 multicast=yes wireless=IEEE 802.11bgn
       ressources: irq:19 portE/S:c000(taille=256) mémoire:d0100000-d0103fff

```

I am quite stuck...
Any help would be appreciated, I have web access through Ethernet but I can't keep the wired connection on the long term.

Thanks a lot :D

---

### Post by nickj6282 on 2012-12-27
I'm having an eminiently similar issue with the XS35V3 and 12.04 that has the RTL8188CE wifi card in it. It can scan and find wireless networks, and it asks for the password when I attempt to connect, but then it goes haywire.

The machine pulls an IP address initially, but I can never actually connect or ping the default gateway or internet addresses. After about two minutes, it loses the IP address and then just prompts for the wifi password over and over for several minutes.

---

### Post by dwb814 on 2012-12-29
Have you tried this?

[http://ubuntuforums.org/showthread.php?p=12427438#post12427438](http://ubuntuforums.org/showthread.php?p=12427438#post12427438)

---

