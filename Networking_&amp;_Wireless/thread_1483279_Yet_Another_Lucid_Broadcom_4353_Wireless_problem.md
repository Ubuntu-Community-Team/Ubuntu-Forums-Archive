---
title: "Yet Another Lucid Broadcom 4353 Wireless problem"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by johnrobert on 2010-05-14
I've been struggling to get my wireless working properly ever since upgrading to Lucid. My problem is erratic connectivity. Frequently I can't see the available networks. And when I can see the available networks, it's 9-to-1 against that I'll be able to connect, instead I just get endlessly prompted for my password. But occasionally it does connect and it works fine in Windows.

I haven't tried a lot yet. I uninstalled my backports. I tried switching from network manager to wicd because that worked once when I was on Kubuntu, but it didn't help this time so I switched back. I'd like to avoid just trying different things before I have some idea that what I'm trying is related to what my problem is.

I would greatly appreciate any help or advice that anyone can offer.

lshw -C network
```
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: c4:17:fe:47:f8:f7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f0a00000-f0a03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 03
       serial: 00:26:b9:21:02:a1
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:35 ioport:7000(size=256) memory:f0804000-f0804fff(prefetchable) memory:f0800000-f0803fff(prefetchable) memory:f0820000-f083ffff(prefetchable)
```

iwconfig
```
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

nmtool eth1
```

NetworkManager Tool

State: connecting

- Device: eth1  [Auto terri-net] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connecting (configuring)
  Default:           no
  HW Address:        C4:17:FE:47:F8:F7

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    terri-net:       Infra, 00:24:01:6A:1F:26, Freq 2452 MHz, Rate 54 Mb/s, Strength 100 WPA
    hpsetup:         Ad-Hoc, 2E:24:81:B7:23:E4, Freq 2437 MHz, Rate 11 Mb/s, Strength 20
    2WIRE153:        Infra, 00:12:88:05:A9:F9, Freq 2437 MHz, Rate 0 Mb/s, Strength 20 WEP
    beachhouse:      Infra, 00:24:56:1E:C3:B1, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WEP
    2WIRE206:        Infra, 00:14:95:B0:F2:A1, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WEP
    beachbungalow:   Infra, 00:25:3C:EB:F9:61, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    The Love Shack:  Infra, 00:18:F8:BD:FB:45, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:26:B9:21:02:A1

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

```

Again, thanks for any direction you can give.

---

### Post by johnrobert on 2010-05-16
I finally seem to have mine working, though it just seems to be a matter of luck and happenstance.

Following instructions I found in some thread or other I opened /etc/NetworkManager/nm-system-settings.conf. Inside that file I edited the entry that read "managed=false" to be "managed=true", then rebooted.

That didn't work. So I changed the setting back to "managed=false" and rebooted. And what I found then was that after my home wireless network failed to auto connect, it would connect when I just chose it manually out of the list of available networks. So I reset my preferences in Network Manager to not attempt an auto connect, and my home network has reliably connected manually ever since.

---

