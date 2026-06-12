---
title: "Network continously disconects in encryption free wireless network area"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by Sachin Gole on 2009-09-17
At home and in my office i have wirelss network connection, At home when i connect it asks password after entering it connects to network and works very well.

At my office its encryption free so no need to enter password or encryption free. it detect network when i select it connects and again after 2 mins it disconect again searches network connects angains same process goes on.

I have Latitude D830 and Ubuntu 8.04 TLS

under System->Administration->Hardware Drivers 
it shows 
Broadcom STA drivers In use.
----------------------------------------------------------------------------------------------
when i do 
ifconfig 
it wont shows wlan0

for this i did following process 
1)Run In Terminal as a power user
         
      # apt-get install    b43-fwcutter
2) And get driver from from internet
        Broadcom-wl-4.80.53.0.tar.gz
      3) Run In Terminal

    # tar  –xvzf     Broadcom-wl-4.80.53.0.tar.gz
    # cd Broadcom-wl-4.80.53.0/kmod/
    #ls 
     wl_apsta.o       wl_apsta_mimo.o
    #b43-fwcutter        -w       /lib/firmware/       wl_apsta.o
    #b43-fwcutter     --unsupported   -w   /lib/firmware/    wl_apsta_mimo.o
    #sync
    #ldconfig
    # init 6  or  # reboot

but this process wont work....

--------------------------------------------------------------------------------------------------
sachin@gole-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:79:b2:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:22:69:4c:7a:ea  
          inet addr:192.168.2.109  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::222:69ff:fe4c:7aea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10158 errors:0 dropped:0 overruns:0 frame:28379
          TX packets:8789 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9637816 (9.1 MB)  TX bytes:1548016 (1.4 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67600 (66.0 KB)  TX bytes:67600 (66.0 KB)

sachin@gole-laptop:~$ 
--------------------------------------------------------------------------------------------------

sachin@gole-laptop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:69:4c:7a:ea
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.2.109 latency=0 module=wl multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:79:b2:7c
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5755m-v3.29 latency=0 link=no module=tg3 multicast=yes port=twisted pair
sachin@gole-laptop:~$ 
------------------------------------------------------------------------------------------------------------------------

sachin@gole-laptop:~$ 
sachin@gole-laptop:~$  lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Quadro NVS 140M [10de:0429] (rev a1)
03:01.0 CardBus bridge [0607]: O2 Micro, Inc. Cardbus bridge [1217:7135] (rev 21)
03:01.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)
sachin@gole-laptop:~$ 
----------------------------------------------------------------------------------------------------------------
If someone already suffered from same problem, Please suggest me solution.

Thanks,
Sachin

---

