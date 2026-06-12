---
title: "aspire 5100 wireless not working  (lshw -c network log here)"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by yoshiki2 on 2009-08-15
I just installed Ubuntu on my aspire 5100, so far wireless is not working. any ideas? lshw log is here:








   raul@ubuntu:~$ lshw -c network
  
  WARNING: you should run this program as super-user.
  
    *-network:0             
  
         description: Ethernet interface
  
         product: RTL-8139/8139C/8139C+
  
         vendor: Realtek Semiconductor Co., Ltd.
  
         physical id: 1
  
         bus info: pci@0000:06:01.0
  
         logical name: eth0
  
         version: 10
  
         serial: 00:16:d4:64:b0:d0
  
         width: 32 bits
  
         clock: 33MHz
  
         capabilities: bus_master cap_list ethernet physical
  
         configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  
    *-network:1
  
         description: Network controller
  
         product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
  
         vendor: Broadcom Corporation
  
         physical id: 2
  
         bus info: pci@0000:06:02.0
  
         version: 02
  
         width: 32 bits
  
         clock: 33MHz
  
         capabilities: bus_master
  
         configuration: driver=b43-pci-bridge latency=64 module=ssb
  
    *-network:0 DISABLED
  
         description: Wireless interface
  
         physical id: 1
  
         logical name: wlan0
  
         serial: 00:19:7d:21:04:6c
  
         capabilities: ethernet physical wireless
  
         configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  
    *-network:1 DISABLED
  
         description: Ethernet interface
  
         physical id: 2
  
         logical name: pan0
  
         serial: 8e:16:50:b3:49:cb
  
         capabilities: ethernet physical
  
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  
  raul@ubuntu:~$

---

### Post by yoshiki2 on 2009-08-15
To run a command as administrator (user "root"), use "sudo <command>".
  
  See "man sudo_root" for details.
  
   
   
  raul@ubuntu:~$ nm-ool
  
  bash: nm-ool: command not found
  
  raul@ubuntu:~$ nm-tool
  
   
   
  NetworkManager Tool
  
   
   
  State: disconnected
  
   
   
  - Device: eth0 -----------------------------------------------------------------
  
    Type:              Wired
  
    Driver:            8139too
  
    State:             unavailable
  
    Default:           no
  
    HW Address:        00:16:D4:64:B0:D0
  
   
   
    Capabilities:
  
      Carrier Detect:  yes
  
      Speed:           10 Mb/s
  
   
   
    Wired Properties
  
      Carrier:         off
  
   
   
   
   
  - Device: wlan0 ----------------------------------------------------------------
  
    Type:              802.11 WiFi
  
    Driver:            b43
  
    State:             disconnected
  
    Default:           no
  
    HW Address:        00:00:00:00:00:00
  
   
   
    Capabilities:
  
   
   
    Wireless Properties
  
      WEP Encryption:  yes
  
      WPA Encryption:  yes
  
      WPA2 Encryption: yes
  
   
   
    Wireless Access Points 
  
   
   
   
   
  raul@ubuntu:~$ iwconfig
  
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
  
   
   
  raul@ubuntu:~$ ping -c 4 google.com
  
  ping: unknown host google.com
  
  raul@ubuntu:~$ ifconfig
  
  eth0      Link encap:Ethernet  HWaddr 00:16:d4:64:b0:d0  
  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
  
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:1000 
  
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
  
            Interrupt:21 Base address:0xa000 
  
   
   
  lo        Link encap:Local Loopback  
  
            inet addr:127.0.0.1  Mask:255.0.0.0
  
            inet6 addr: ::1/128 Scope:Host
  
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
  
            RX packets:16 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:0 
  
            RX bytes:1040 (1.0 KB)  TX bytes:1040 (1.0 KB)
  
   
   
  raul@ubuntu:~$ netstat -r
  
  Kernel IP routing table
  
  Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
  
  raul@ubuntu:~$ sudo lshw -c network
  
  [sudo] password for raul: 
  
    *-network:0             
  
         description: Ethernet interface
  
         product: RTL-8139/8139C/8139C+
  
         vendor: Realtek Semiconductor Co., Ltd.
  
         physical id: 1
  
         bus info: pci@0000:06:01.0
  
         logical name: eth0
  
         version: 10
  
         serial: 00:16:d4:64:b0:d0
  
         size: 10MB/s
  
         capacity: 100MB/s
  
         width: 32 bits
  
         clock: 33MHz
  
         capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
  
         configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  
    *-network:1
  
         description: Network controller
  
         product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
  
         vendor: Broadcom Corporation
  
         physical id: 2
  
         bus info: pci@0000:06:02.0
  
         version: 02
  
         width: 32 bits
  
         clock: 33MHz
  
         capabilities: bus_master
  
         configuration: driver=b43-pci-bridge latency=64 module=ssb
  
    *-network:0 DISABLED
  
         description: Wireless interface
  
         physical id: 2
  
         logical name: wlan0
  
         serial: 00:19:7d:21:04:6c
  
         capabilities: ethernet physical wireless
  
         configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  
    *-network:1 DISABLED
  
         description: Ethernet interface
  
         physical id: 3
  
         logical name: pan0
  
         serial: d6:8a:8d:23:02:b1
  
         capabilities: ethernet physical
  
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  
  raul@ubuntu:~$ lspci
  
  00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
  
  00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
  
  00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
  
  00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
  
  00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
  
  00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
  
  00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
  
  00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
  
  00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
  
  00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
  
  00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
  
  00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
  
  00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
  
  00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
  
  00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
  
  00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
  
  00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
  
  01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
  
  06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
  
  06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
  
  06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
  
  06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
  
  06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
  
  06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
  
  06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
  
  raul@ubuntu:~$ 
  
  raul@ubuntu:~$

---

### Post by yoshiki2 on 2009-08-16
bump

---

