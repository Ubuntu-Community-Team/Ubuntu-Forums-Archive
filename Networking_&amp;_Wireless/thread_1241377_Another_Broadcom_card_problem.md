---
title: "Another Broadcom card problem"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by TBlake on 2009-08-15
Sorry to beat a dead horse.  I've tried several of the tutorials on how to install the wireless card on my system with no success.
Here's the info I have.  I'm running Ubuntu 9.04.  My system is a Dell Inspiron B130 laptop.  My wireless card Dell calls a WLAN 1370 WLAN MiniPCI Card.
I was able to get this info from the terminal:
taylor@taylor-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

taylor@taylor-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:8c:7a:fb  
          inet addr:192.168.0.142  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fe8c:7afb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4613 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5671351 (5.6 MB)  TX bytes:710257 (710.2 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

taylor@taylor-laptop:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

taylor@taylor-laptop:~$ 

Anybody have a solution or should I just abandon it and use some other wireless solution?

Thanks

---

### Post by spd106 on 2009-08-16
The Dell wireless 1370 card has been well supported in Ubuntu for a while now. However due to license restrictions it won't work out of the box, instead you need to download some firmware. 

The System -> Administration -> Hardware Drivers utility should fetch and install the driver firmware for you as long as you have a wired connection available. 

Otherwise, installing the [b43-fwcutter]("apturl:b43-fwcutter") package will also fetch the driver firmware.

For more info see
[http://linuxwireless.org/en/users/Drivers/b43#firmware_installation](http://linuxwireless.org/en/users/Drivers/b43#firmware_installation)

---

### Post by TBlake on 2009-08-16
The active light is now on.  Progress!  I just have to figure out how to make it connect to my in-home wireless network.

---

### Post by TBlake on 2009-08-21
Still dumbfounded.  I'm probably missing something incredibly simple.  Followed a few procedures in other forum posts with no luck.  Based on a similar question, here's all the relevant info (I think).  My wireless network is working for the rest of my house (running XP).  The ESSID is being broadcast.  But I click on the network icon (the two computers in the upper right) and there are no networks showing.
```

taylor@taylor-laptop:~$ sudo -s
[sudo] password for taylor: 
root@taylor-laptop:~# sudo aptitude install hwinfo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  hwinfo libhd15{a} 
0 packages upgraded, 2 newly installed, 0 to remove and 189 not upgraded.
Need to get 718kB of archives. After unpacking 1978kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com jaunty/universe libhd15 15.3-1ubuntu1 [673kB]
Get:2 http://us.archive.ubuntu.com jaunty/universe hwinfo 15.3-1ubuntu1 [44.9kB]
Fetched 718kB in 2s (339kB/s)
Selecting previously deselected package libhd15.
(Reading database ... 102008 files and directories currently installed.)
Unpacking libhd15 (from .../libhd15_15.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package hwinfo.
Unpacking hwinfo (from .../hwinfo_15.3-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up libhd15 (15.3-1ubuntu1) ...

Setting up hwinfo (15.3-1ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

root@taylor-laptop:~# hwinfo --netcard
08: PCI 203.0: 0282 WLAN controller                             
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_14e4_4318
  Unique ID: y9sn.IOGU8m+1vhF
  Parent ID: 6NW+.InKz0bgid89
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:02:03.0
  SysFS BusID: 0000:02:03.0
  Hardware Class: network
  Model: "Broadcom BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller"
  Vendor: pci 0x14e4 "Broadcom"
  Device: pci 0x4318 "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x0005 
  Revision: 0x02
  Driver: "b43-pci-bridge"
  Driver Modules: "ssb"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xdfbfe000-0xdfbfffff (rw,non-prefetchable)
  IRQ: 17 (136 events)
  HW Address: 00:90:4b:e7:cf:05
  Link detected: no
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 14
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472 2.484
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v000014E4d00004318sv00001028sd00000005bc02sc80i00"
  Driver Info #0:
    Driver Status: ssb is active
    Driver Activation Cmd: "modprobe ssb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #12 (PCI bridge)

09: PCI 200.0: 0200 Ethernet controller
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_14e4_170c
  Unique ID: rBUF.bF3aAoTmvN9
  Parent ID: 6NW+.InKz0bgid89
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: network
  Model: "Broadcom BCM4401-B0 100Base-TX"
  Vendor: pci 0x14e4 "Broadcom"
  Device: pci 0x170c "BCM4401-B0 100Base-TX"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x01c9 
  Revision: 0x02
  Driver: "b44"
  Driver Modules: "ssb", "b44"
  Device File: eth0
  Memory Range: 0xdfbfc000-0xdfbfdfff (rw,non-prefetchable)
  IRQ: 18 (964 events)
  HW Address: 00:14:22:8c:7a:fb
  Link detected: yes
  Module Alias: "pci:v000014E4d0000170Csv00001028sd000001C9bc02sc00i00"
  Driver Info #0:
    Driver Status: b44 is active
    Driver Activation Cmd: "modprobe b44"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #12 (PCI bridge)
root@taylor-laptop:~# udo iwlist scanning
The program 'udo' is currently not installed.  You can install it by typing:
apt-get install udo
bash: udo: command not found
root@taylor-laptop:~# sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

root@taylor-laptop:~# sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:8c:7a:fb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.70 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:e7:cf:05
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: b2:d3:a7:68:d4:32
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@taylor-laptop:~# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 [8086:2666] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
root@taylor-laptop:~# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@taylor-laptop:~# uname -a
Linux taylor-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
root@taylor-laptop:~# dmesg | grep ound
[    0.679564] ACPI: No dock devices found.
[    0.738571] pnp: PnP ACPI: found 11 devices
[    1.655986] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.656220] pcieport-driver 0000:00:1c.3: found MSI capability
[    2.039867] isapnp: No Plug & Play device found
[    2.372128] hub 1-0:1.0: USB hub found
[    2.372554] hub 2-0:1.0: USB hub found
[    2.372888] hub 3-0:1.0: USB hub found
[    2.373220] hub 4-0:1.0: USB hub found
[    2.373572] hub 5-0:1.0: USB hub found
[    2.376234] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.378721] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.068091] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0
[    3.140094] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[   10.906123] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   11.047464] b43-phy0: Broadcom 4318 WLAN found
[   11.416389] lp: driver loaded but no devices found
root@taylor-laptop:~# dmesg | grep witch
[    0.020919] SMP alternatives: switching to UP code
[    1.195988] Switched to high resolution mode on CPU 0
[    1.676482] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.677185] ACPI: Lid Switch [LID]
root@taylor-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

root@taylor-laptop:~# 


```

---

### Post by spd106 on 2009-08-24
I think you would catch the relevant information if you filter dmesg with b43. 
As an example, my PC has the following output.

```
$ dmesg | grep b43
[    4.154910] b43-pci-bridge 0000:01:0a.0: PCI INT A -> Link[APC1] -> GSI 16 (level, high) -> IRQ 16
[   11.711992] b43-phy0: Broadcom 4306 WLAN found
[   26.158810] input: b43-phy0 as /devices/virtual/input/input5
[   26.192030] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   26.330515] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   26.371159] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   26.418889] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   26.604030] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   26.670511] Registered led device: b43-phy0::tx
[   26.670533] Registered led device: b43-phy0::rx
[   26.670555] Registered led device: b43-phy0::radio
[   26.684032] b43-phy0: Radio turned on by software

```

---

### Post by TBlake on 2009-08-24
I ended up also trolling the IRC chats and someone suggested reinstalling the firmware.  Did that.  Then checked in BIOS if my card was turned on.  Apparently with linux, the ON light does not necessarily mean that the card is on.  Switched the card on and presto, everything is fantastic.

---

