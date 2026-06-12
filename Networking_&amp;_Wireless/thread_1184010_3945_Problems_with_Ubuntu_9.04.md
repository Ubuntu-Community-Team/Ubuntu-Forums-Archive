---
title: "3945 Problems with Ubuntu 9.04"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by DrDmoney on 2009-06-10
Hello, I am very new to Linux... I have played with it before, but only a little... I am now wanting to crack WEP and possibly WPA but I have been running into dead walls because I really don't know the hell I am doing... I get confused very easy with linux, but still want to give it a chance...

Now to my problems...

Alright I have a Gateway C142XL that uses Intel 3945ABG network card, but I have not been able to get it to work. I don't know even how to install drivers...I don't know how to work with the terminal... I don't know how to become root, I don't know how to make a driver into a exicutible package.... I am truely lost... I hope that someone will help be out more then say use google...Thank you

   lspci
  
  ```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
  
  00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
  
  00:19.0 Ethernet controller: Intel Corporation 82566MC Gigabit Network Connection (rev 03)
  
  00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
  
  00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
  
  00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
  
  00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
  
  00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
  
  00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
  
  00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
  
  00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
  
  00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
  
  00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
  
  00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
  
  00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
  
  00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
  
  00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
  
  01:00.0 VGA compatible controller: ATI Technologies Inc M71 [Mobility Radeon X2100] (Secondary) (rev ce)
  
  02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
  
  03:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
  
  03:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
  
  03:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
  
  03:09.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```
   
  lsusb
  
  ```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  
  Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
  Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
  Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  
  Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
  
  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
  Bus 003 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
  
  Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
   
  ifconfig
  
  ```
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:d0:54:dd  
  
            inet6 addr: fe80::2e0:b8ff:fed0:54dd/64 Scope:Link
  
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
  
            RX packets:360 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:1000 
  
            RX bytes:42182 (42.1 KB)  TX bytes:5724 (5.7 KB)
  
            Memory:f8500000-f8520000 
  
   
   
  lo        Link encap:Local Loopback  
  
            inet addr:127.0.0.1  Mask:255.0.0.0
  
            inet6 addr: ::1/128 Scope:Host
  
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
  
            RX packets:4 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:0 
  
            RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
  
```
   
   
  iwconfig
  
  ```
lo        no wireless extensions.
  
   
   
  eth0      no wireless extensions.
  
   
   
  pan0      no wireless extensions.
  
```
   
   
  lshw -c network
  
  ```
WARNING: you should run this program as super-user.
  
    *-network               
  
         description: Ethernet interface
  
         product: 82566MC Gigabit Network Connection
  
         vendor: Intel Corporation
  
         physical id: 19
  
         bus info: pci@0000:00:19.0
  
         logical name: eth0
  
         version: 03
  
         serial: 00:e0:b8:d0:54:dd
  
         width: 32 bits
  
         clock: 33MHz
  
         capabilities: bus_master cap_list ethernet physical
  
         configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.3-0 latency=0 module=e1000e multicast=yes
  
    *-network UNCLAIMED
  
         description: Network controller
  
         product: PRO/Wireless 3945ABG [Golan] Network Connection
  
         vendor: Intel Corporation
  
         physical id: 0
  
         bus info: pci@0000:02:00.0
  
         version: 02
  
         width: 32 bits
  
         clock: 33MHz
  
         capabilities: cap_list
  
         configuration: latency=0
  
    *-network DISABLED
  
         description: Ethernet interface
  
         physical id: 1
  
         logical name: pan0
  
         serial: 7a:8e:1c:6d:bd:62
  
         capabilities: ethernet physical
  
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  
  
```

---

### Post by DrDmoney on 2009-06-10
Bumb

---

