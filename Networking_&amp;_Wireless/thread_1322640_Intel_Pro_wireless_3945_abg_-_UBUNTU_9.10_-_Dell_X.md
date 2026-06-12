---
title: "Intel Pro wireless 3945 abg - UBUNTU 9.10 - Dell Xps M1530 Not working"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by mrcet007 on 2009-11-11
Intel Pro wireless 3945 abg not working in ubuntu 9.10. Some times after 5 to 6 times restarting it works,but its very annoying.
One thing i noticed when i examined **dmesg out put** is 

[   17.306353] iwl3945 0000:0b:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   17.328189] iwl3945 0000:0b:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   17.350025] iwl3945 0000:0b:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   22.282739] iwl3945 0000:0b:00.0: Error: saturation power is -1, less than minimum expected 40
[   22.282743] iwl3945 0000:0b:00.0: Invalid power index
[   22.282748] iwl3945 0000:0b:00.0: initializing driver failed
[   22.282776] iwl3945 0000:0b:00.0: PCI INT A disabled
[   22.282792] iwl3945: probe of 0000:0b:00.0 failed with error -5
Does this mean anything to you Linux geeks ?Pls Help

Here are my other details required

```
dmesg

FFFFFF
[   17.306353] iwl3945 0000:0b:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   17.328189] iwl3945 0000:0b:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   17.350025] iwl3945 0000:0b:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   22.282739] iwl3945 0000:0b:00.0: Error: saturation power is -1, less than minimum expected 40
[   22.282743] iwl3945 0000:0b:00.0: Invalid power index
[   22.282748] iwl3945 0000:0b:00.0: initializing driver failed
[   22.282776] iwl3945 0000:0b:00.0: PCI INT A disabled
[   22.282792] iwl3945: probe of 0000:0b:00.0 failed with error -5
[   22.426900] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input13
[   22.624250] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   22.624350] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   22.624421] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   23.434570] EXT4-fs (sda5): barriers enabled
[   23.478877] kjournald2 starting: pid 899, dev sda5:8, commit interval 5 seconds
[   23.492081] EXT4-fs (sda5): internal journal on sda5:8
[   23.492089] EXT4-fs (sda5): delayed allocation enabled
[   23.492096] EXT4-fs: file extents enabled
[   23.492179] EXT4-fs: mballoc enabled
[   23.492204] EXT4-fs (sda5): mounted filesystem with ordered data mode
[   24.157119] __ratelimit: 6 callbacks suppressed
[   24.157123] type=1505 audit(1257927625.451:13): operation="profile_replace" pid=960 name=/usr/share/gdm/guest-session/Xsession
[   24.159198] type=1505 audit(1257927625.451:14): operation="profile_replace" pid=961 name=/sbin/dhclient3
[   24.161166] type=1505 audit(1257927625.455:15): operation="profile_replace" pid=961 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   24.161646] type=1505 audit(1257927625.455:16): operation="profile_replace" pid=961 name=/usr/lib/connman/scripts/dhclient-script
[   24.166126] type=1505 audit(1257927625.459:17): operation="profile_replace" pid=962 name=/usr/bin/evince
[   24.180273] type=1505 audit(1257927625.471:18): operation="profile_replace" pid=962 name=/usr/bin/evince-previewer
[   24.188467] type=1505 audit(1257927625.479:19): operation="profile_replace" pid=962 name=/usr/bin/evince-thumbnailer
[   24.199771] type=1505 audit(1257927625.491:20): operation="profile_replace" pid=964 name=/usr/lib/cups/backend/cups-pdf
[   24.200825] type=1505 audit(1257927625.491:21): operation="profile_replace" pid=964 name=/usr/sbin/cupsd
[   24.203833] type=1505 audit(1257927625.495:22): operation="profile_replace" pid=965 name=/usr/sbin/mysqld-akonadi
[   28.511812] sky2 eth0: enabling interface
[   28.512309] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   32.109697] ppdev: user-space parallel port driver
[   32.156255] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   32.156259] Bluetooth: BNEP filters: protocol multicast
[   32.164241] Bridge firewalling registered
[   34.721071] CE: hpet increasing min_delta_ns to 15000 nsec
[   71.081117] usb 7-2: USB disconnect, address 2
[   71.081124] usb 7-2.1: USB disconnect, address 3
[   71.081759] usb 7-2.2: USB disconnect, address 4
[   71.113586] usb 7-2.3: USB disconnect, address 5

```

```
deepak@Deepak-Laptop:~$ lsmod |grep iwl
iwl3945                77212  0 
iwlcore               112508  1 iwl3945
mac80211              181236  2 iwl3945,iwlcore
led_class               4096  3 iwl3945,iwlcore,sdhci
cfg80211               93052  3 iwl3945,iwlcore,mac80211
```

```
deepak@Deepak-Laptop:~$ lspci


00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
**0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)**

```

```
deepak@Deepak-Laptop:~$ lsusb
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```
deepak@Deepak-Laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:3f:2d:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2400 (2.4 KB)  TX bytes:2400 (2.4 KB)
```

```
deepak@Deepak-Laptop:~$ sudo lshw -C network
[sudo] password for deepak: 
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:3f:2d:69
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:f1ffc000-f1ffffff ioport:de00(size=256)
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f1eff000-f1efffff

```
```
deepak@Deepak-Laptop:~$  iwconfig wlan0
wlan0     No such device
```

---

