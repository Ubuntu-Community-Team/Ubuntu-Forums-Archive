---
title: "wireless not working but it says it is"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by thesikness on 2008-12-19
every now and then after an update and reboot i need to fix my wireless, which is no big deal. but this time it just stopped working without ever updating. i did the usual fix ([http://ubuntuforums.org/showthread.php?t=792158&highlight=madwifi+no+target](http://ubuntuforums.org/showthread.php?t=792158&highlight=madwifi+no+target)) and it said that the wireless was working fine. it had the little network bar in the top right corner and it said i was connected to the modem. but the connection isn't working at all even though it says it is. i couldn't find anything on this. if anybody can help, i really appreciate it. i'd be happy to post the outputs of any codes. thanks.

---

### Post by pytheas22 on 2008-12-19
Please post the output of these commands at a time when the connection says it's working but really isn't:
```

lspci -nn
lsusb
ifconfig
sudo iwlist scan
lshw -C Network
wget google.com
wget 74.125.45.100
```

---

### Post by thesikness on 2008-12-20
> **pytheas22 said:**
> Please post the output of these commands at a time when the connection says it's working but really isn't:
```

lspci -nn
lsusb
ifconfig
sudo iwlist scan
lshw -C Network
wget google.com
wget 74.125.45.100
```

(lspci -nn) shook@shook-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
0c:04.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
0c:04.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
0c:04.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
0c:04.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]

(lsusb) shook@shook-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

(ifconfig) shook@shook-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1b:9e:9b:ba:58  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:9eff:fe9b:ba58/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46848 (45.7 KB)  TX bytes:21806 (21.2 KB)

eth0      Link encap:Ethernet  HWaddr 00:1e:ec:33:4e:0b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1507 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1511398 (1.4 MB)  TX bytes:306629 (299.4 KB)
          Interrupt:218 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1844 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:92200 (90.0 KB)  TX bytes:92200 (90.0 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1B-9E-9B-BA-58-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3084 errors:0 dropped:0 overruns:0 frame:0
          TX packets:467 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:294536 (287.6 KB)  TX bytes:39629 (38.7 KB)
          Interrupt:18 

(sudo iwlist scan) shook@shook-laptop:~$ sudo iwlist scan
[sudo] password for shook: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:13:46:0A:4C:04
                    ESSID:"default"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-64 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

(lshw -C Network) shook@shook-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:33:4e:0b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wifi0
       version: 01
       serial: 00:1b:9e:9b:ba:58
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.0.104 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

(wget google.com) shook@shook-laptop:~$ wget google.com
--20:27:36--  [http://google.com/](http://google.com/)
           => `index.html'
Resolving google.com... failed: Name or service not known.

(wget 74.125.45.100) shook@shook-laptop:~$ wget 74.125.45.100
--20:28:37--  [http://74.125.45.100/](http://74.125.45.100/)
           => `index.html'
Connecting to 74.125.45.100:80... failed: Connection timed out.


hope that helps. sorry it took a while to get back to you.

---

### Post by pytheas22 on 2008-12-20
hmmm, that's all very strange...you definitely have an IP address and by all indications it looks like you should be able to access the Internet.  But when you try to pull google.com, it can't be reached.

Could you please try recompiling your madwifi driver using the script in [this thread]("http://ubuntuforums.org/showthread.php?t=798485")?  The thread you were using before installs an outdated snapshot of the driver, I think, but this new thread should install the latest code.  That may help (after reinstalling the driver using the script, you will need to reboot for the new driver to take effect).  If not, we can look at other things, like using [wicd]("http://wicd.sourceforge.net") instead of Network Manager.

---

