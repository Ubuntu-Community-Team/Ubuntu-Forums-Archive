---
title: "Intel Centrino wireless-n 1000 freeze at login"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by bluebear on 2011-09-21
Hi! 

Been trying to run ubuntu on my asus a7t. I had to change 
wifi pci-e card. I have a switch on the left side to turn  wifi & bluetooth on and off. If this switch is on, the computer freezes about the time the login screen comes up. 
In recovery i get these lines before it freezes: 
```
iwlagn 0000:01:00.0: Could not load the INST uCode section
iwlagn 0000:01:00.0: Unable to set up bootstrap uCode: -110 
iwlagn 0000:01:00.0: Could not load the INST uCode section
iwlagn 0000:01:00.0: Unable to set up bootstrap uCode: -110 
iwlagn 0000:01:00.0: Could not load the INST uCode section
iwlagn 0000:01:00.0: Unable to set up bootstrap uCode: -110 
iwlagn 0000:01:00.0: Could not load the INST uCode section
iwlagn 0000:01:00.0: Unable to set up bootstrap uCode: -110 
iwlagn 0000:01:00.0: Could not load the INST uCode section
iwlagn 0000:01:00.0: Unable to set up bootstrap uCode: -110 
iwlagn 0000:01:00.0: Unable to initialise device after 5 attempts.
```

It then freezes and I have to hold powerbutton to shutdown. 
Tried 11.04 and 10.10, starting to think my card is broken. Have not tried in windows.  

rfkill list 
```
hmlrs@asus:~$ rfkill list
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```

lspci 
```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTra                                     nsport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address                                      Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Con                                     troller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscella                                     neous Control
01:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
04:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce Go 7600] (rev                                      a1)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Et                                     hernet (rev 10)
05:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapte                                     r (rev 19)
05:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (re                                     v 0a)
05:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

```

iwconfig
```
hmlrs@asus:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

lshw -C network
```
 hmlrs@asus:~$ sudo lshw -C network
       *-network DISABLED
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:64:04:bd:a8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-30-generic firmware=128.50.3.1 build 13488 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:43 memory:dcffe000-dcffffff
  *-network
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 10
       serial: 00:18:f3:f7:b6:ca
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.106 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:18 ioport:e800(size=256) memory:dffffc00-dffffcff memory:dffc0000-dffdffff

```

Any pointers would be appreciated, perhaps I have to bite the bullet and see if it works in windows. 

Cheers, 
bluebear.

---

### Post by praseodym on 2011-09-21
Try to reinstall the kernel:

```
sudo apt-get install --reinstall linux-image-$(uname -r) linux-headers-$(uname -r) dkms build-essential
```
and reboot. You may want to check the BIOS settings for wifi and/or reset the BIOS to default settings.

---

### Post by bluebear on 2011-09-22
The BIOS doesn´t contain anything about wifi. It is very
sparse, setting wise. I loaded defaults just in case. 

Still freezes at login. 

Tried re-installing the kernel, but sorry to say, it still freezes.

---

### Post by praseodym on 2011-09-22
Try the newest driver with linux-wireless:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
make clean
make
sudo make install  
```
and reboot.

---

### Post by bluebear on 2011-09-22
Thanks, I will try that. Seems [www.intellinuxwireless.org](www.intellinuxwireless.org) is down at the moment. I will post back when it comes up again.

---

