---
title: "Can see wireless networks but can't connect"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by cierin on 2009-02-23
Hello everyone,
I've searched around on the forums and google for a while, but I can't fix my problem. I've been able to connect to wireless until this afternoon, when it suddenly stopped working. I can still see the wireless network, but I can't connect. 

Here are the outputs:
lspci 
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c) 
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) 
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02) 01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) 
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) 
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) 
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12) 
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12) 
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) 
```

ifconfig 
```
eth0      Link encap:Ethernet  HWaddr 00:1c:23:8f:4b:38   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:17  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2286 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2286 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:114300 (111.6 KB)  TX bytes:114300 (111.6 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:1c:26:3a:4c:60   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:4469 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:877010 (856.4 KB)  TX bytes:16742 (16.3 KB) 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-1C-26-3A-4C-60-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
```
iwconfig 
```
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wmaster0  no wireless extensions. 
 
wlan0     IEEE 802.11g  ESSID:""   
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:6A:9C:A4:80    
          Bit Rate=11 Mb/s   Tx-Power=27 dBm    
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B    
          Link Quality=85/100  Signal level=-43 dBm  Noise level=-69 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
```
sudo lshw -C network 
  ```
*-network                
       description: Network controller 
       product: BCM4311 802.11b/g WLAN 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:0c:00.0 
       version: 01 
       width: 32 bits 
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
       serial: 00:1c:23:8f:4b:38 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s 
  *-network 
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:1c:26:3a:4c:60 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 
```
sudo iwlist scan 
```
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 
 
wmaster0  Interface doesn't support scanning. 
 
wlan0     Scan completed : 
          Cell 01 - Address: 00:14:6A:9C:A4:80 
                    ESSID:"wireless" 
                    Mode:Master 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=85/100  Signal level=-44 dBm  Noise level=-71 dBm 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:tsf=000003b7561860cf 
          Cell 02 - Address: 00:0D:3A:29:49:01 
                    ESSID:"L310" 
                    Mode:Master 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=48/100  Signal level=-78 dBm  Noise level=-71 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                              12 Mb/s; 48 Mb/s 
                    Extra:tsf=000001228114ec3a 
          Cell 03 - Address: 00:0F:8F:4A:02:40 
                    ESSID:"wireless" 
                    Mode:Master 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=48/100  Signal level=-78 dBm  Noise level=-71 dBm 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:tsf=000003b75675e5e1 

```

I'm not sure what the L310 is. I'm trying to connect to wireless. I'm not sure why there are two wirelesses coming up here, but only one in the network connection thing in the gui.

I've tried the following, as per [this thread]("http://ubuntuforums.org/showthread.php?t=571194"):
```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "wireless"
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0
```

When I do that, it's all good up until the last command, where this happens:
```
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1c:26:3a:4c:60
Sending on   LPF/wlan0/00:1c:26:3a:4c:60
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I dual boot Windows, and I went in to make sure that Window's power settings weren't disabling my wireless, as suggested in [this thread]("http://ubuntuforums.org/showpost.php?p=5024425&postcount=1").

Would someone please give me a suggestion for where to look next?

Thanks!

---

