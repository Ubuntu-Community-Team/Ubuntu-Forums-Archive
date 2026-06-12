---
title: "Can't use wireless network on HP G50 laptop - Ubuntu 8.10"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by sevensevens on 2009-02-21
I just purchased an HP G50 laptop, and cannot get wireless networking functional (wired networking is fine though).  I've grabbed backports for ibex + installed NDISwrapper - no luck.  I believe the network driver may be installed, but disabled (I have a network LED that refuses to turn green).  I've poked around with lspci and such, and have posted relevant bits here.

# lspci
```

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

# lsusb
```

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


# lshw -C network
```

  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:61:bd:b5
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.10.109 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fe:2d:52:ea:79:ba
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

# iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


```

---

### Post by sevensevens on 2009-02-22
I think the problem has something to do with this line from lshw

```

*-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fe:2d:52:ea:79:ba
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by sdegrace on 2009-02-27
I'm in the same boat as you. I won't install Ubuntu from the Live CD unless the wireless is working. I hope there is a solution, because I have gotten used to Ubuntu on my old laptop and I'll slit my wrists if I have to start working in Vista. I will post if I find and answer, although I don't think I'll do better than you have.

Stephen

---

### Post by sdegrace on 2009-03-01
Dude, I solved it! I got the answer from this post:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6669937](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6669937)

You have to follow the directions to install linux-backports-modules-intrepid like so:

```
$ sudo apt-get update
$ sudo apt-get install linux-backports-modules-intrepid
```

After I rebooted, bingo, my wireless was working *perfectly*! I'm posting this from the wireless right now! The LED is still red, but I don't care about that.

The back story here is that I actually said to hell with it and installed 8.10 on spec figuring that I would figure out the wireless later... figured out that madwifi.org is now moved to madwifi-project.org... built and installed various versions of ath_pci... even toyed with Fedora (freezes during LiveCD boot), OpenSUSE (still downloading on my other computer) and Hardy (DON'T do Hardy on this model laptop. The nVidia driver 8.04 wants you to install causes you to have a blank screen. It's way more trouble than it's worth). Then stumbled across this simple solution while I was waiting for OpenSUSE to download. Now I am pretty much 100% satisfied!

---

### Post by sevensevens on 2009-03-26
:( still no luck - my HP is a G50-126NR

---

### Post by sdegrace on 2009-03-26
I have a G50-209CA. Here is the output of lspci for you - hope it helps! Let me know if there's anything else I can do.

Stephen

```

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation Device 075e (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation Device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation Device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
02:00.0 VGA compatible controller: nVidia Corporation Device 0845 (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

---

### Post by TpyKv on 2009-04-06
> **sdegrace said:**
> Dude, I solved it! I got the answer from this post:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6669937](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6669937)

You have to follow the directions to install linux-backports-modules-intrepid like so:

```
$ sudo apt-get update
$ sudo apt-get install linux-backports-modules-intrepid
```

After I rebooted, bingo, my wireless was working *perfectly*! I'm posting this from the wireless right now! The LED is still red, but I don't care about that.

The back story here is that I actually said to hell with it and installed 8.10 on spec figuring that I would figure out the wireless later... figured out that madwifi.org is now moved to madwifi-project.org... built and installed various versions of ath_pci... even toyed with Fedora (freezes during LiveCD boot), OpenSUSE (still downloading on my other computer) and Hardy (DON'T do Hardy on this model laptop. The nVidia driver 8.04 wants you to install causes you to have a blank screen. It's way more trouble than it's worth). Then stumbled across this simple solution while I was waiting for OpenSUSE to download. Now I am pretty much 100% satisfied!

This worked for me!! Incredible, I tried everything, compiling the new drivers didnt work, only this - three cheers!!

---

### Post by tagra123 on 2010-01-10
For ubuntu HARDY 8.04 this is what to use

```
sudo apt-get update
sudo apt-get install linux-backports-modules-hardy
```

---

