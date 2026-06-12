---
title: "wifi"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by acespade on 2009-01-30
just installed kubuntu to full hard drive how do i install my broadcam 4306 wireless lan card to kubuntu? any pleh

---

### Post by Ayuthia on 2009-01-30
If you have a working internet connection in Kubuntu, you can go into System->Administration->Hardware Drivers and select the Broadcom driver.  Say yes to have it fetch the firmware for you.  You should then reboot and it should be ready.

---

### Post by acespade on 2009-01-30
no luck i have ubuntu 8.10 now not kubuntu when i go to the drivers it just says graphics driver but i do have this can you help??


ace@ace-laptop:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

ace@ace-laptop:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  Type:              Wired
  Driver:            NULL(info.linux.driver)
  State:             connected
  Default:           yes
  HW Address:        00:19:B9:82:AA:31

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Settings

  IPv4 Settings:
    Address:         74.128.198.74
    Prefix:          20 (255.255.240.0)
    Gateway:         74.128.192.1

    DNS:             74.128.17.114
    DNS:             74.128.19.102


ace@ace-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ace@ace-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:82:aa:31  
          inet addr:74.128.198.74  Bcast:74.128.207.255  Mask:255.255.240.0
          inet6 addr: fe80::219:b9ff:fe82:aa31/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:374350 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59860 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:180075677 (180.0 MB)  TX bytes:4734085 (4.7 MB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

ace@ace-laptop:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4306 802.11a Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:82:aa:31
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=74.128.198.74 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1e:dc:5a:25:1c:dd
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ace@ace-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4306 802.11a Wireless LAN Controller (rev 03)
ace@ace-laptop:~$ lsusb
Bus 006 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ace@ace-laptop:~$ uname -a
Linux ace-laptop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
ace@ace-laptop:~$ dmesg|grep ound
[    2.577724] pnp: PnP ACPI: found 12 devices
[    6.366140] pcieport-driver 0000:00:05.0: found MSI capability
[    6.367017] pcieport-driver 0000:00:07.0: found MSI capability
[    6.726138] isapnp: No Plug & Play device found
[    6.962020] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    9.557184] No dock devices found.
[    9.925898] hub 1-0:1.0: USB hub found
[   10.089875] hub 2-0:1.0: USB hub found
[   10.268075] hub 3-0:1.0: USB hub found
[   10.533810] hub 4-0:1.0: USB hub found
[   10.702248] hub 5-0:1.0: USB hub found
[   12.484596] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[   12.498202] hub 6-0:1.0: USB hub found
[   12.777307] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
[   13.397501] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   30.708251] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[   31.071305] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   37.537807] lp: driver loaded but no devices found
[   46.687144] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-56 processors (2 cpu cores) (version 2.20.00)
[   47.975114] apm: BIOS not found.
[   56.272452] mtrr: base(0xe0000000) is not aligned on a size(0xc000000) boundary
ace@ace-laptop:~$ dmesg|grep etect
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] Detected 798.216 MHz processor.
[    6.955634] EISA: Detected 0 cards.
[    9.925949] hub 1-0:1.0: 2 ports detected
[   10.089926] hub 2-0:1.0: 2 ports detected
[   10.268121] hub 3-0:1.0: 2 ports detected
[   10.533860] hub 4-0:1.0: 2 ports detected
[   10.702295] hub 5-0:1.0: 2 ports detected
[   12.498261] hub 6-0:1.0: 10 ports detected

---

### Post by Ayuthia on 2009-01-30
Let's go ahead and try to install b43-fwcutter.  It is the same thing as Hardware drivers.  You should be able to install it through Synaptic or if you want to use the Terminal:
```
sudo apt-get install b43-fwcutter
```

---

### Post by acespade on 2009-01-31
thank you now wut do i  do after that?
should i paste the output in the terminal and let you see what it said it asked me to ectract so i did

---

### Post by Ayuthia on 2009-01-31
Can you go into the Terminal and check if you can see any wireless sites:
```
sudo iwlist scan
```

---

### Post by acespade on 2009-01-31
ace@ace-laptop:~$ sudo iwlist scan
[sudo] password for ace: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

---

### Post by Ayuthia on 2009-01-31
> **acespade said:**
> ace@ace-laptop:~$ sudo iwlist scan
[sudo] password for ace: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

It is looking like you might need to go the ndiswrapper route.  Before you do that, can you post the results of:
```
dmesg|b43
```

Here is the guide that has been the most successful with ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Reiger on 2009-01-31
Well, unless you made sure to issue
```

sudo modprobe b43

```
 before you checked the result of iwlist (whether or not it shows a wireless device at all) you can't 'judge' that total lack of output.

Before you try to use ndiswrapper you may want to try [compat wireless dirvers]("http://linuxwireless.org/en/users/Download") (it lists the b43 driver among the supported ones).

---

### Post by Ayuthia on 2009-02-01
> **Reiger said:**
> Well, unless you made sure to issue
```

sudo modprobe b43

```
 before you checked the result of iwlist (whether or not it shows a wireless device at all) you can't 'judge' that total lack of output.

Before you try to use ndiswrapper you may want to try [compat wireless dirvers]("http://linuxwireless.org/en/users/Download") (it lists the b43 driver among the supported ones).

The link you provided is for the b43 module.  The 4306 rev 03 card has been having problems with connecting in Ubuntu lately and I have not been able to tell if it is because of Network Manager or changes made to the module.

---

