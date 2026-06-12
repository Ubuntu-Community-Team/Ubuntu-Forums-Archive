---
title: "unable to turn on wifi,even though wifi driver is present"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by saiki4116 on 2011-02-08
[IMG]http://E:/e-disc&downloads/ubuntu_help/error/error.png[/IMG]hi,
i installed ubuntu 10.10 on my dell inspiron14r(n4010) using WUBI.
i installed ubuntu in seperate partition of 20 gb.

then i installed broadcom wifi driver,and wifi is working except that i have to get connected to network in win7.So to overcome this problem i installed wicd,after that in network manager there is no option for enabling wireless,so i removed wicd and reinstalled network manager,but even then the problem persists.Then i searched in net,and found out that wicd can be used as network manager,so i removed network manager completly and installed wicd.but even then the problem persists,here the terminal outputs for various networking commands,and i have also including the screenshot of the condition of broadcomm wifi driver... 


```
saikiran@ubuntu:~$ sudo rfkill list 
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


saikiran@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


saikiran@ubuntu:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device


saikiran@ubuntu:~$ sudo lshw -businfo
Bus info          Device      Class          Description
========================================================
                              system         Inspiron N4010
                              bus            0P8P1W
                              memory         123KiB BIOS
cpu@0                         processor      Intel(R) Core(TM) i5 CPU       M 45
                              memory         128KiB L1 cache
                              memory         512KiB L2 cache
                              memory         3MiB L3 cache
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              memory         4GiB System Memory
                              memory         2GiB SODIMM Synchronous 1333 MHz (0
                              memory         2GiB SODIMM Synchronous 1333 MHz (0
cpu@1                         processor      
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
                              processor      Logical CPU
pci@0000:00:00.0              bridge         Core Processor DRAM Controller
pci@0000:00:01.0              bridge         Core Processor PCI Express x16 Root
pci@0000:02:00.0              display        Manhattan [Mobility Radeon HD 5000 
pci@0000:02:00.1              multimedia     Manhattan HDMI Audio [Mobility Rade
pci@0000:00:16.0              communication  5 Series/3400 Series Chipset HECI C
pci@0000:00:1a.0              bus            5 Series/3400 Series Chipset USB2 E
pci@0000:00:1b.0              multimedia     5 Series/3400 Series Chipset High D
pci@0000:00:1c.0              bridge         5 Series/3400 Series Chipset PCI Ex
pci@0000:00:1c.1              bridge         5 Series/3400 Series Chipset PCI Ex
pci@0000:04:00.0              network        BCM4313 802.11b/g LP-PHY
pci@0000:00:1c.5              bridge         5 Series/3400 Series Chipset PCI Ex
pci@0000:05:00.0  eth0        network        AR8152 v1.1 Fast Ethernet
pci@0000:00:1d.0              bus            5 Series/3400 Series Chipset USB2 E
pci@0000:00:1e.0              bridge         82801 Mobile PCI Bridge
pci@0000:00:1f.0              bridge         Mobile 5 Series Chipset LPC Interfa
pci@0000:00:1f.2  scsi0       storage        5 Series/3400 Series Chipset 6 port
scsi@0:0.0.0      /dev/sda    disk           320GB ST9320325AS
scsi@0:0.0.0,1    /dev/sda1   volume         360MiB Windows FAT volume
scsi@0:0.0.0,2    /dev/sda2   volume         10118MiB Windows NTFS volume
scsi@0:0.0.0,3    /dev/sda3   volume         59GiB Windows NTFS volume
scsi@0:0.0.0,4    /dev/sda4   volume         228GiB Extended partition
                  /dev/sda5   volume         20GiB HPFS/NTFS partition
                  /dev/sda6   volume         208GiB HPFS/NTFS partition
scsi@1:0.0.0      /dev/cdrom  disk           DVD+-RW DS-8A4S
pci@0000:00:1f.3              bus            5 Series/3400 Series Chipset SMBus 
pci@0000:00:1f.6              generic        5 Series/3400 Series Chipset Therma
pci@0000:ff:00.0              bridge         Core Processor QuickPath Architectu
pci@0000:ff:00.1              bridge         Core Processor QuickPath Architectu
pci@0000:ff:02.0              bridge         Core Processor QPI Link 0
pci@0000:ff:02.1              bridge         Core Processor QPI Physical 0
pci@0000:ff:02.2              bridge         Core Processor Reserved
pci@0000:ff:02.3              bridge         Core Processor Reserved
                              power          SANYO
                              system         
                              power          To Be Defined By O.E.M




saikiran@ubuntu:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0300000-f0303fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: c1
       serial: b8:ac:6f:5a:6f:a6
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:48 memory:f0200000-f023ffff ioport:3000(size=128)


saikiran@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
	Subsystem: Dell Device 0456
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: cfe00000-cfefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Dell Device 0456
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f0406800 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
	Subsystem: Dell Device 0456
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at f0407000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
	Subsystem: Dell Device 0456
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: c0000000-c01fffff
	Prefetchable memory behind bridge: 00000000c0200000-00000000c03fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: f0300000-f03fffff
	Prefetchable memory behind bridge: 00000000c0400000-00000000c05fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f0200000-f02fffff
	Prefetchable memory behind bridge: 00000000c0600000-00000000c07fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
	Subsystem: Dell Device 0456
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0407400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
	Subsystem: Dell Device 0456
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06) (prog-if 01 [AHCI 1.0])
	Subsystem: Dell Device 0456
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
	I/O ports at 1818 [size=8]
	I/O ports at 180c [size=4]
	I/O ports at 1810 [size=8]
	I/O ports at 1808 [size=4]
	I/O ports at 1820 [size=32]
	Memory at f0406000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
	Subsystem: Dell Device 0456
	Flags: medium devsel, IRQ 10
	Memory at f0407800 (64-bit, non-prefetchable) [size=256]
	I/O ports at 1840 [size=32]
	Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
	Subsystem: Dell Device 0456
	Flags: fast devsel, IRQ 18
	Memory at f0405000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: intel ips
	Kernel modules: intel_ips

02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] (prog-if 00 [VGA controller])
	Subsystem: Dell Device 0456
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at cfee0000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 2000 [size=256]
	[virtual] Expansion ROM at cfe00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
	Subsystem: Dell Device 0456
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at cfedc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
	Subsystem: Dell Device 0010
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at f0300000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: wl

05:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
	Subsystem: Dell Device 0456
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at f0200000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 3000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: atl1c
	Kernel modules: atl1c

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Intel Corporation Device 8086
	Flags: bus master, fast devsel, latency 0



saikiran@ubuntu:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:5a:6f:a6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:48 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:175888 (175.8 KB)  TX bytes:175888 (175.8 KB)


saikiran@ubuntu:~$ sudo iwlist <eth0> scan
bash: eth0: No such file or directory
```




can anyone sugest how to make wicd to turn on wifi,and scan wifi n/w....
the network i am trying to connect is an acces point and without any encrypted password

---

### Post by Brandon Williams on 2011-02-09
There are known problems with Broadcom 43XX on Ubuntu 10.10. Did you read [this post](http://ubuntuforums.org/showthread.php?t=1604868) in order to attempt to resolve your problem.

FWIW ... the issue is not network-manager or wicd related. They aren't letting you use your card because the system doesn't know about it. I suggest that you go back to network-manager and follow the suggestions in the other thread in order to resolve the issue.

---

### Post by saiki4116 on 2011-02-11
mine is broadcom 4313,i have installed  linux broadcom sta source,which is in restricted drivers,and after clicked additional drivers,i can see that the driver is active, but not in use even after turning on wifi,and the wifi switch is hardware or software blocked..

---

### Post by Brandon Williams on 2011-02-11
[Here](http://ubuntuforums.org/showpost.php?p=10283164&postcount=12) is another suggestion for getting 4313 cards working on 10.10.

The restricted drivers gui doesn't list 4313 as one of the supported chipsets for the STA driver. Are you sure it's supposed to work with that card? My 10.10 machine has a 4312 card, which is listed as supported and works just fine.

---

### Post by saiki4116 on 2011-02-15
sorry for not replying,the problem is that wifi is not working properly is because i installed ubuntu using wubi.now i have installed ubuntu as dual boot.wifi is working but the problem it is not showing available access points,but if i logon to windows connect to  a access point,then restart my lappy,to logon to ubuntu then it is connecting to wifi accesspoint.

---

### Post by northd_tech on 2011-08-30
I found these blocks of text at a couple of windows driver sites, but it might be a helpful reference for people trying to get Dell laptops running Broadcom wireless setups for their **lspci -vvnn | grep 14e4** terminal commands:

>   
[LIST]
[*][FONT=Calibri]DELL TRUEMOBILE 1300 WLAN      MINI-PCI CARD [PCI\VEN_14E4&DEV_4318] [/FONT]
[/LIST]
  
[LIST]
[*][FONT=Calibri]DELL TRUEMOBILE 1300 WLAN      MINI-PCI CARD [PCI\VEN_14E4&DEV_4320&SUBSYS_00011028] [/FONT]
[/LIST]
  
[LIST]
[*][FONT=Calibri]DELL TRUEMOBILE 1300 WLAN      MINI-PCI CARD [PCI\VEN_14E4&DEV_4320] [/FONT]
[*][FONT=Calibri]DELL TRUEMOBILE 1300 WLAN PC      CARD [PCI\VEN_14E4&DEV_4320&SUBSYS_00021028] [/FONT]
[*][FONT=Calibri]DELL TRUEMOBILE 1400 DUAL      BAND WLAN MINI-PCI CARD [PCI\VEN_14E4&DEV_4319] [/FONT]
[*][FONT=Calibri]DELL TRUEMOBILE 1400 DUAL      BAND WLAN MINI-PCI CARD [PCI\VEN_14E4&DEV_4324&SUBSYS_00011028] [/FONT]
[*][FONT=Calibri]DELL TRUEMOBILE 1400 DUAL      BAND WLAN MINI-PCI CARD [PCI\VEN_14E4&DEV_4324] [/FONT]
[*][FONT=Calibri]DELL TRUEMOBILE 1400 DUAL      BAND WLAN PC CARD [PCI\VEN_14E4&DEV_4324&SUBSYS_00021028] [/FONT]
[*][FONT=Calibri]DELL WIRELESS 1350 WLAN      MINI-PCI CARD [PCI\VEN_14E4&DEV_4320&SUBSYS_00031028] [/FONT]
[*][FONT=Calibri]DELL WIRELESS 1350 WLAN PC      CARD [PCI\VEN_14E4&DEV_4320&SUBSYS_00041028] [/FONT]
[*][FONT=Calibri]DELL WIRELESS 1370 WLAN      MINI-PCI CARD [PCI\VEN_14E4&DEV_4318&SUBSYS_00051028] [/FONT]
[*][FONT=Calibri]DELL WIRELESS 1370 WLAN PC      CARD [PCI\VEN_14E4&DEV_4318&SUBSYS_00061028] [/FONT]
[*][FONT=Calibri]DELL WIRELESS 1390 WLAN      EXPRESSCARD [PCI\VEN_14E4&DEV_4311&SUBSYS_00081028] [/FONT]
[*][FONT=Calibri]DELL WIRELESS 1390 WLAN      MINI-CARD [PCI\VEN_14E4&DEV_4311&SUBSYS_00071028] [/FONT]
[*][FONT=Calibri]DELL WIRELESS 1390 WLAN      MINI-CARD [PCI\VEN_14E4&DEV_4311] [/FONT]
[*][FONT=Calibri]DELL WIRELESS 1450 DUAL BAND      WLAN MINI-PCI CARD [PCI\VEN_14E4&DEV_4324&SUBSYS_00031028] [/FONT]
[*][FONT=Calibri]DELL WIRELESS 1450 DUAL BAND      WLAN PC CARD [PCI\VEN_14E4&DEV_4324&SUBSYS_00041028] [/FONT]
[*][FONT=Calibri]DELL WIRELESS 1470 DUAL BAND      WLAN MINI-PCI CARD [PCI\VEN_14E4&DEV_4319&SUBSYS_00051028] [/FONT]
[*][FONT=Calibri]DELL WIRELESS 1470 DUAL BAND      WLAN PC CARD [PCI\VEN_14E4&DEV_4319&SUBSYS_00061028] [/FONT]
[*][FONT=Calibri]DELL WIRELESS 1490 DUAL BAND      WLAN EXPRESSCARD [PCI\VEN_14E4&DEV_4312&SUBSYS_00081028] [/FONT]
[*][FONT=Calibri]DELL WIRELESS 1490 DUAL BAND      WLAN MINI-CARD [PCI\VEN_14E4&DEV_4312&SUBSYS_00071028] [/FONT]
[*][FONT=Calibri]DELL WIRELESS 1490 DUAL BAND      WLAN MINI-CARD [PCI\VEN_14E4&DEV_4312] [/FONT]
[*][FONT=Calibri]DELL WIRELESS 1500 DRAFT      802.11N WLAN MINI-CARD [PCI\VEN_14E4&DEV_4328&SUBSYS_00091028] [/FONT]
[*][FONT=Calibri]DELL WIRELESS 1500 DRAFT      802.11N WLAN MINI-CARD [PCI\VEN_14E4&DEV_4328] [/FONT]
[*][FONT=Calibri]DELL WIRELESS 1505 DRAFT      802.11N WLAN MINI-CARD [PCI\VEN_14E4&DEV_4328&SUBSYS_000A1028] [/FONT]
[/LIST]
  >   [FONT=Calibri] Broadcom 802.11 MULTIBAND NETWORK ADAPTER PCI/VEN_14E4&DEV_4314[/FONT]
  [FONT=Calibri]Broadcom 802.11A NETWORK ADAPTER PCI/VEN_14E4&DEV_4316[/FONT]
  [FONT=Calibri]BROADCOM 802.11A NETWORK ADAPTER PCI/VEN_14E4&DEV_431A[/FONT]
  [FONT=Calibri]BROADCOM 802.11A NETWORK ADAPTER PCI/VEN_14E4&DEV_4321&REV_03[/FONT]
  [FONT=Calibri]BROADCOM 802.11B NETWORK ADAPTER PCI/VEN_14E4&DEV_4303[/FONT]
  [FONT=Calibri]BROADCOM 802.11G NETWORK ADAPTER PCI/VEN_1095&DEV_0670[/FONT]
  [FONT=Calibri]BROADCOM 802.11G NETWORK ADAPTER PCI/VEN_14E4&DEV_4313[/FONT]
  [FONT=Calibri]BROADCOM 802.11N NETWORK ADAPTER PCI/VEN_14E4&DEV_4322[/FONT]
  [FONT=Calibri]BROADCOM 802.11N NETWORK ADAPTER PCI/VEN_14E4&DEV_4329[/FONT]
  [FONT=Calibri]BROADCOM 802.11N NETWORK ADAPTER PCI/VEN_14E4&DEV_432A[/FONT]
  [FONT=Calibri]BROADCOM 802.11N NETWORK ADAPTER PCI/VEN_14E4&DEV_432B[/FONT]
  [FONT=Calibri]BROADCOM 802.11N NETWORK ADAPTER PCI/VEN_14E4&DEV_432C[/FONT]
  [FONT=Calibri]BROADCOM 802.11N NETWORK ADAPTER PCI/VEN_14E4&DEV_4340[/FONT]
  [FONT=Calibri]BROADCOM 802.11N NETWORK ADAPTER PCI/VEN_14E4&DEV_4341[/FONT]
  [FONT=Calibri]BROADCOM 802.11N NETWORK ADAPTER PCI/VEN_14E4&DEV_4350[/FONT]
  [FONT=Calibri]BROADCOM 802.11N NETWORK ADAPTER PCI/VEN_14E4&DEV_4351[/FONT]
  [FONT=Calibri]BROADCOM 802.11N NETWORK ADAPTER PCI/VEN_14E4&DEV_4353[/FONT]
  [FONT=Calibri]BROADCOM 802.11N NETWORK ADAPTER PCI/VEN_14E4&DEV_4357[/FONT]
  [FONT=Calibri]BROADCOM 802.11N NETWORK ADAPTER PCI/VEN_14E4&DEV_4716[/FONT]
  [FONT=Calibri]BROADCOM 802.11N NETWORK ADAPTER PCI/VEN_14E4&DEV_4722[/FONT]
  [FONT=Calibri]BROADCOM 802.11N NETWORK ADAPTER PCI/VEN_14E4&DEV_A8D6[/FONT]
  [FONT=Calibri]BROADCOM 802.11N NETWORK ADAPTER PCI/VEN_14E4&DEV_A8D8[/FONT]
  [FONT=Calibri]Dell TRUEMOBILE 1300 WLAN MINI-PCI CARD PCI/VEN_14E4&DEV_4318[/FONT]
  [FONT=Calibri]Dell TRUEMOBILE 1300 WLAN MINI-PCI CARD PCI/VEN_14E4&DEV_4320&REV_03[/FONT]
  [FONT=Calibri]DELL TRUEMOBILE 1400 DUAL BAND WLAN MINI-PCI CARD PCI/VEN_14E4&DEV_4319[/FONT]
  [FONT=Calibri]DELL TRUEMOBILE 1400 DUAL BAND WLAN MINI-PCI CARD PCI/VEN_14E4&DEV_4324&REV_03[/FONT]
  [FONT=Calibri]DELL wireless 1390 WLAN MINI-CARD PCI/VEN_14E4&DEV_4311[/FONT]
  [FONT=Calibri]DELL wireless 1395 WLAN MINI-CARD PCI/VEN_14E4&DEV_4315[/FONT]
  [FONT=Calibri]DELL WIRELESS 1490 DUAL BAND WLAN MINI-CARD PCI/VEN_14E4&DEV_4312[/FONT]
  [FONT=Calibri]DELL WIRELESS 1500 DRAFT 802.11N WLAN MINI-CARD PCI/VEN_14E4&DEV_4328[/FONT]
  I also found this handy Broadcom Linux driver troubleshooting reference at the Fedora forum:

```
                               lspci -vvnn | grep 14e4
                                         |
                                Any of these listed?
                                        4301
                                        4303
                                        4306
                                        4309
                                        4311
                                        4312
                                        4313 
                                        4318
                                       /    \
                                      /      \
                                     /        \
                                    /          \
                                  Yes           No
                                  /              \
                                 /                \
                                /                  \
                             lsmod                4310?
                              /                   /   \
                             /                   /     \
                            /                  Yes      No
                          b43                  /         \
                        loaded?               /           \
                        /    \           ndiswrapper   4321,43224
                       /      No                        4322,43225
                      /        \                         4328,43227
                     /          \                         43XG,43228
                   Yes       b43legacy                      /   \
                   /          loaded?                      /     \
                  /           /     \                    Yes      No
                 /          Yes      No                  /         \
                /           /         \                 /           \
             4306?         /         4311?        broadcom-wl      4320?
            4311?      Install        4312?                     (from lsusb
           4318?      version 3        4313?                   or other means)
           /   \      firmware         /   \                        /    \
          /     \                     /     \                      /      \
        Yes      No                 Yes      No                  Yes       No
        /         \                 /         \                  /          \
       /           \               /           \                /            \
b43-openfwwf     Install     broadcom-wl   ndiswrapper    b43-openfwwf   ndiswrapper
    or          version 4                                       or
  Install       firmware                                    rndis_wlan
 version 4
 firmware
 -------------------------------------------------------------------------------------
```There is also an excellent troubleshooting guide at that Fedora forum (but some of the commands would need 'translation' for Debian and Ubuntu).  It is still an EXCELLENT reference to use for Broadcom wireless interfaces though.

 [http://www.fedoraforum.org/forum/showthread.php?t=239922](http://www.fedoraforum.org/forum/showthread.php?t=239922)

Here are a few more 'required reading' references for Broadcom cards too:

 [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
  
Broadcom's proprietary "STA" driver:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Linuxwireless.org "b43" Broadcom page
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

EDIT:  Also, here is the "WiFi" search engine:
[http://www.x11wifi.com/wifi.php?q=Broadcom](http://www.x11wifi.com/wifi.php?q=Broadcom)

---

