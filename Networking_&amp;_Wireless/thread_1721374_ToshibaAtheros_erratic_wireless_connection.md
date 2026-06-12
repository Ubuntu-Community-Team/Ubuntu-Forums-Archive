---
title: "Toshiba/Atheros erratic wireless connection"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by pcar916 on 2011-04-04
Hi Folks,
I've done my best to give you all info now. Let me know if there needs to be more. I'm relatively new to LINUX and am excited to learn more. This is a persistent problem

The problem: Erratic INITIAL wireless connection 
    - Once it's connected, it stays that way during that session
    - When logged off, or suspended it might reconnect... or not. No detectable pattern so far
    - Once it has failed, I can boot the Windows 7 partition and the  wireless adapter has been disabled and requires a manual reconnection.

One of three conditions exists
1. Sometimes it connects instantly. Roughly 10 percent of the time
2. Sometimes it tries to connect but eventually gives me the opportunity  to type in the network key... this might work but not always
    - In this case the wireless adapter never connects
    - The adapter sees no wireless networks at all
3. Sometimes the wireless connection will not even try to connect to the  AT&T router (red exclamation mark on the wireless icon)
    - Then I have to manually connect to a hidden network, which it always remembers. This sometimes works but not always
    - Ubuntu restart might not fix the problem, but usually not

Note: I can get it to work 100% of the time by removing the battery and restarting the computer

What have I done so far?
1. I've deleted and recreated the hidden SSID several times on the Toshiba
2. I have loaded the driver for another Atheros AR9xxx chipset found in another thread... no change in behavior

I have not:
    - Diagnosed the router firmware since this only happens on one computer
    - Created a static network address scheme (non DHCP)

Thanks in advance for the assistance,
Ron
____________________________________________________________________________________
Environment:
Toshiba Satellite A
Turion 64x2 (dual processor AMD)
Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
Maverick Meerkat 10.10 Fully updated
Gnome 2.32.0 (9/27/2010)
Dual-boot to Windows 7 Ultimate (64 bit)

Network: AT&T Router / hidden SSID / DHCP / 3 Windows XP laptops, this laptop, and 1 wired dual boot XP/Lucid Lynx Ubuntu machine

Only the Toshiba has the problem.

____________________________________________________________________________________________
First an lspci readout, since it's common, then diagnostics are included below in 2 cases
1. Not trying to connect
2. Connected

Commands issued: 
lspci
iwconfig
ifconfig
sudo lshw -C network

____________________________________________________________________________________________
sudo lspci

sudo lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
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
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

Inserted expanded wireless data:
14:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
        Subsystem: Askey Computer Corp. Device 7128
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at f8200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath5k
        Kernel modules: ath5k

1a:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
1a:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
1a:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
1a:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
______________________________________________________________________________________________________________________________
______________________________________________________________________________________________________________________________

Condition: Not trying to connect

ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40416 (40.4 KB)  TX bytes:40416 (40.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:37:6d:4a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
__________________________________________________________________

iwconfig


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
___________________________________________________________________


sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:1c:bb:91
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=no multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:a000(size=256) memory:f8300000-f8300fff memory:84400000-8441ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:37:6d:4a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-28-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f8200000-f820ffff
____________________________________________________________________________________________________________________________________________________
____________________________________________________________________________________________________________________________________________________
Condition: Connected

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:38:1c:bb:91  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:492 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39120 (39.1 KB)  TX bytes:39120 (39.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:37:6d:4a  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:9eff:fe37:6d4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3700 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3741672 (3.7 MB)  TX bytes:584775 (584.7 KB)
____________________________________________________________________

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"fake-name"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: B0:E7:54:C6:7D:E9   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
______________________________________________________________________

sudo lshw -C network
 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:1c:bb:91
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:43 ioport:a000(size=256) memory:f8300000-f8300fff memory:84400000-8441ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:37:6d:4a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-28-generic firmware=N/A ip=192.168.1.70 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f8200000-f820ffff

---

