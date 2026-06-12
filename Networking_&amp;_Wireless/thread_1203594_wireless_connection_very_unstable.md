---
title: "wireless connection very unstable"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by rose34 on 2009-07-03
Hi everyone,

I have recently returned from university, bringing my computer with me. At uni, my ubuntu installation worked fine on our wireless network, but now I have it at home the connection seems very unstable. It will go from speeds of 100kbps - 4kbps, and frequently lose connection altogether. I have not changed anything on my computer since getting home, and is much closer to the router physically than the windows pc I am writing this on, which enjoys a constant speed of about 85kbps.

Does anyone have any suggestions as to what could be wrong?

Thanks!
Joe

---

### Post by pytheas22 on 2009-07-03
I would suspect a problem with your wireless driver.  If you could please post the output of the following commands, I'll know which driver you're using, and can probably find an alternative that may work better:
```

lspci -nn
lsusb
lshw -C Network
uname -rm
iwconfig
```

---

### Post by rose34 on 2009-07-03
lspci -nn results:
> 
joe@joe-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:0314]
00:00.1 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:1314]
00:00.2 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:2314]
00:00.3 Host bridge [0600]: VIA Technologies, Inc. PT890 Host Bridge [1106:3208]
00:00.4 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:4314]
00:00.7 Host bridge [0600]: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge [1106:7314]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8237/VX700 PCI Bridge [1106:b198]
00:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
00:09.0 Communication controller [0780]: Agere Systems V.92 56K WinModem [11c1:048c] (rev 03)
00:0b.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller [1106:3044] (rev 80)
00:0f.0 IDE interface [0101]: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller [1106:3149] (rev 80)
00:0f.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 81)
00:10.4 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 86)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] [1106:3227]
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
01:00.0 VGA compatible controller [0300]: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] [1106:3344] (rev 01)


---

### Post by rose34 on 2009-07-03
lsusb results:
> 
joe@joe-desktop:~$ lsusb
Bus 001 Device 004: ID 1bcf:0c31 Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 13b1:0011 Linksys WUSB54GP v4.0 802.11g Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


lshw -C Network results:
> 
joe@joe-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:f7:2a:0d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:12:17:7d:d5:b0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.4 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: c6:d1:00:cc:fd:9a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


---

### Post by rose34 on 2009-07-03
uname results:
> 
joe@joe-desktop:~$ uname -rm
2.6.28-11-generic i686


iwconfig:

> 
joe@joe-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1E:2A:1D:E0:E6   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=66/100  Signal level:-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


---

### Post by pytheas22 on 2009-07-03
Thanks for the information.  I think your card might work better if you used ndiswrapper, which allows you to drive it using the Windows driver, instead of Ubuntu's default driver.  To ndiswrapper set up for your device, run these commands while connected to the Internet (be careful not to make typos; if possible, you should copy and paste the commands to be safe):
```

sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
wget http://www.burnthesorbonne.com/files/13b1_0011_win32.tar.gz
tar -xzvf 13b1_0011_win32.tar.gz 
sudo ndiswrapper -i rt2500usb.inf 
echo -e 'blacklist rt2500usb\nblacklist rt2500pci\nblacklist rt61pci\nblacklist rt2x00pci\nblacklist rt2400pci\nblacklist rt2x00lib\nblacklist rt2x00usb' | sudo tee -a /etc/modprobe.d/blacklist.conf
echo ndiswrapper | sudo tee -a /etc/modules
```

Then reboot, and hopefully the connection will work better.  If not, let me know.

---

### Post by rose34 on 2009-07-04
thanks a lot, that seems to have done the trick.


once again, I'm reminded why I love Ubuntu - the speed and helpfulness of other uses in assisting with problems!

Cheers,
Joe

---

### Post by gb2k01 on 2009-08-24
> **pytheas22 said:**
> Thanks for the information.  I think your card might work better if you used ndiswrapper, which allows you to drive it using the Windows driver, instead of Ubuntu's default driver.  To ndiswrapper set up for your device, run these commands while connected to the Internet (be careful not to make typos; if possible, you should copy and paste the commands to be safe):
```

sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
wget http://www.burnthesorbonne.com/files/13b1_0011_win32.tar.gz
tar -xzvf 13b1_0011_win32.tar.gz 
sudo ndiswrapper -i rt2500usb.inf 
echo -e 'blacklist rt2500usb\nblacklist rt2500pci\nblacklist rt61pci\nblacklist rt2x00pci\nblacklist rt2400pci\nblacklist rt2x00lib\nblacklist rt2x00usb' | sudo tee -a /etc/modprobe.d/blacklist.conf
echo ndiswrapper | sudo tee -a /etc/modules
```

Then reboot, and hopefully the connection will work better.  If not, let me know.

Sorry to add on to a solved issue, but I'm having the same trouble. Is it possible to just use the above code you listed, or does it have to specifically tailored to my router/wireless card? Thanks for the help!!!

And I agree with the original poster on why I, too, love Ubuntu.

---

### Post by hathiphnath on 2009-08-24
I have [exactly the same issue]("http://ubuntuforums.org/showthread.php?t=1248388") too. :(

---

### Post by gb2k01 on 2009-08-24
> **hathiphnath said:**
> I have [exactly the same issue]("http://ubuntuforums.org/showthread.php?t=1248388") too. :(

Good luck to both of us!! I'll let you know if I figure anything out :)

---

### Post by hathiphnath on 2009-08-24
Do we have the same wireless cards? Mine is listed in my signature. I fear that our solutions might be different with different cards.

---

### Post by gb2k01 on 2009-08-24
I use an Intel: Intel Wireless WiFi Link 4965AGN 

On the above instructions (for the NdisWrapper), it sounds like if we want to do that, you need to connect to a land-line, otherwise it could muck up the whole thing. I found that information here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Also the SourceForge page lists compatibility with some devices, but I don't see mine listed (under Documentation heading):

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page)

I may just give it a shot in a few days, though I always have that nagging worry I'll manage to entirely break my internet. Life without the internet... sounds miserable!!!

---

### Post by pytheas22 on 2009-08-24
> Is it possible to just use the above code you listed, or does it have to specifically tailored to my router/wireless card? Thanks for the help!!!

You need to make sure you're installing the right driver for your wireless card.  If you could please post the output of these commands, I can try to find the driver you need:
```

lspci -nn
lsusb
```

gb2k01, I don't think ndiswrapper will support iwl4965 cards.  But there may be other ways to solve your problem (which is that your connection is flaky?).  If you could post the output of these commands, it would be helpful:
```

dmesg | grep -e iwl -e wlan
uname -rm
cat /etc/issue
lshw -C Network
iwconfig
```

---

### Post by hathiphnath on 2009-08-24
Here's my output of those two commands:
 
lspci -nn:
```
00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 10)
00:01.0 PCI bridge [0604]: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port [8086:29c1] (rev 10)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 9500 GT [10de:0640] (rev a1)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
04:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
```

lsusb:
```
Bus 001 Device 002: ID 18a5:0214  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by gb2k01 on 2009-08-24
> **pytheas22 said:**
> You need to make sure you're installing the right driver for your wireless card.  If you could please post the output of these commands, I can try to find the driver you need:
```

lspci -nn
lsusb
```

gb2k01, I don't think ndiswrapper will support iwl4965 cards.  But there may be other ways to solve your problem (which is that your connection is flaky?).  If you could post the output of these commands, it would be helpful:
```

dmesg | grep -e iwl -e wlan
uname -rm
cat /etc/issue
lshw -C Network
iwconfig
```

Hey pytheas,

Yes the connection issue is that it is flaky and will randomly cut out then come back again, and that it'll go from fast to slow pretty quickly. Anyway, here's the output for the commands. Thanks for your help, if I was anywhere near Baltimore I'd treat you to some coffee, maybe next time!

```

lspci -nn
lsusb
```
Produced:
```
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
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
08:07.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
08:07.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
08:07.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
```

And:
```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:1839 Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 044e:3012 Alps Electric Co., Ltd 
Bus 003 Device 004: ID 044e:3013 Alps Electric Co., Ltd 
Bus 003 Device 003: ID 044e:3010 Alps Electric Co., Ltd 
Bus 003 Device 002: ID 044e:3011 Alps Electric Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

The rest:

```
[    9.314538] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[    9.314541] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[    9.314643] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.314677] iwlagn 0000:02:00.0: setting latency timer to 64
[    9.314763] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[    9.357427] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[    9.357499] iwlagn 0000:02:00.0: irq 2299 for MSI/MSI-X
[    9.358470] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   22.691409] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   22.963725] Registered led device: iwl-phy0:radio
[   22.963752] Registered led device: iwl-phy0:assoc
[   22.963785] Registered led device: iwl-phy0:RX
[   22.963804] Registered led device: iwl-phy0:TX
[   22.989255] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.415271] wlan0: authenticate with AP 00:0e:a6:26:80:c4
[   24.417318] wlan0: authenticated
[   24.417322] wlan0: associate with AP 00:0e:a6:26:80:c4
[   24.419480] wlan0: RX AssocResp from 00:0e:a6:26:80:c4 (capab=0x401 status=0 aid=1)
[   24.419485] wlan0: associated
[   24.440783] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   24.464654] wlan0: disassociating by local choice (reason=3)
[   34.968069] wlan0: no IPv6 routers present
[   55.393723] wlan0: authenticate with AP 00:24:01:45:97:74
[   55.397724] wlan0: authenticated
[   55.397729] wlan0: associate with AP 00:24:01:45:97:74
[   55.402087] wlan0: RX AssocResp from 00:24:01:45:97:74 (capab=0x431 status=0 aid=2)
[   55.402092] wlan0: associated
[ 7959.922908] wlan0: authenticate with AP 00:24:01:45:97:74
[ 7959.927236] wlan0: authenticated
[ 7959.927247] wlan0: associate with AP 00:24:01:45:97:74
[ 7959.930943] wlan0: RX AssocResp from 00:24:01:45:97:74 (capab=0x431 status=0 aid=2)
[ 7959.930951] wlan0: associated
[ 7959.951378] wlan0: disassociating by local choice (reason=3)
[ 8036.332468] wlan0: deauthenticated
[ 8174.689213] wlan0: authenticate with AP 00:24:01:45:97:74
[ 8174.691934] wlan0: authenticated
[ 8174.691946] wlan0: associate with AP 00:24:01:45:97:74
[ 8174.697058] wlan0: RX ReassocResp from 00:24:01:45:97:74 (capab=0x431 status=0 aid=2)
[ 8174.697066] wlan0: associated
```

```
greg@greg-laptop:~$ uname -rm
2.6.28-15-generic i686
```

```
greg@greg-laptop:~$ cat /etc/issue
Ubuntu 9.04 \n \l
```

```
greg@greg-laptop:~$ lshw -C Network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1f:3b:0e:1e:ab
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.109 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:80:7e:c8:1e
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:64:53:90:fe:ad
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

```
greg@greg-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"alma"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:24:01:45:97:74   
          Bit Rate=60 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-7 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

That's all of it, sorry for the massive quantity :(

---

### Post by bkratz on 2009-08-24
> **gb2k01 said:**
> Hey pytheas,

Yes the connection issue is that it is flaky and will randomly cut out then come back again, and that it'll go from fast to slow pretty quickly. Anyway, here's the output for the commands. Thanks for your help, if I was anywhere near Baltimore I'd treat you to some coffee, maybe next time!




I have an interesting question (at least to me!) and Pytheas might be the only that can answer this.  Since the transmission is just Flaky and I notice that you have a wireless mouse which I looked up and see that it operates at primary frequency 27.045 Mhz and secondary at 27.145 Mhz could it be that it is disrupting the communications with the router.  My telephone sure does even though I moved channels several times. Just curious.

---

### Post by Topher88 on 2009-08-24
I'd like to try out ndiswrapper if I can as well, or any other solution that you might have, because I'm having the same problem; the internet works great in some locations, but at others, such as on campus, it is extremely unstable.  Here is my information:

```

chris@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

``````

chris@ubuntu:~$ lsusb
Bus 002 Device 002: ID 5986:0180 Acer, Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

``````

chris@ubuntu:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:5c:58:14
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=10.193.213.223 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:d8:5c:c7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 4e:80:fa:6f:75:b1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

``````

chris@ubuntu:~$ uname -rm
2.6.28-14-generic x86_64

``````

chris@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.

```

---

### Post by Topher88 on 2009-08-24
Please?  lol

---

### Post by pytheas22 on 2009-08-25
**hathiphnath**: please try these commands:
```

sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
wget http://launchpadlibrarian.net/13909160/Driver_1097_2KXP_0201.tar.gzsudo
tar -xzvf Driver_1097_2KXP_0201.tar.gz
sudo ndiswrapper -i Driver_1097_2KXP_0201/WINXP/net8185.inf 
echo ndiswrapper | sudo tee -a /etc/modules
echo blacklist rtl8187 | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist rtl8150 | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist rtl8180 | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo update-initramfs -k all -u
```

Then reboot and see what happens.  If this doesn't help, please post the output of:
```

dmesg | grep -e ndis -e wlan
uname -rm
lshw -C Network
ndiswrapper -l
```
[B]
gb2k01[/B]: two suggestions for you: 1.) try using wicd instead of NetworkManager.  Sometimes wicd works better.  To install wicd, type:
```

sudo apt-get install wicd
```

Then launch it from the Applications>Internet menu.  See if it does a better job maintaining your connection.  (If it doesn't and you want NM back, just type 'sudo apt-get install network-manager-gnome').

If wicd doesn't help, you should try compiling a new version of wireless driver in order to get the most recent code.  To do that, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2."  Save it to your desktop. Then run these commands:
```

sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make
sudo make unload
sudo make load
sudo make install
```

Then reboot and see if the new version of the driver works better.
> 
I have an interesting question (at least to me!) and Pytheas might be the only that can answer this. Since the transmission is just Flaky and I notice that you have a wireless mouse which I looked up and see that it operates at primary frequency 27.045 Mhz and secondary at 27.145 Mhz could it be that it is disrupting the communications with the router. My telephone sure does even though I moved channels several times. Just curious.

Great suggestion, bkratz.  Interference is also definitely something to keep in mind, and can contribute to flaky connections.  If none of the above helps either of you, it could be worth switching your router to different channels to see if that helps.  Try to pick a channel that none of your neighbors is using.  Also try to move your router and wireless cards as far as possible from sources of interference, like phones, bluetooth stuff, etc.

I dealt with this on my own network just last week, incidentally...connection kept dropping, but I moved the router to broadcast on a different channel and things are much better now.

**Topher88**: I couldn't find Windows drivers for your card (but I didn't have time to search exhaustively).  If you could please provide a link to the .exe or .zip file that you used to install drivers for your card in Windows, we can give ndiswrapper a try.  I'm not sure it will work, but it's the only other option on your wireless card besides the 'wl' driver, which is a proprietary driver from Broadcom (and therefore difficult to fix without waiting Broadcom's help).

---

### Post by hathiphnath on 2009-08-25
> **pytheas22 said:**
> Then reboot and see what happens.  If this doesn't help, please post the output of:Now it can't find wireless at all. :( Here's my output.

```
kelly@Huntloom:~$ dmesg | grep -e ndis -e wlan
[    7.094854] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[    7.155866] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[    7.155873] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8185'
[    7.156221] ndiswrapper (load_wrap_driver:108): couldn't load driver net8185; check system log for messages from 'loadndisdriver'
[    7.156272] usbcore: registered new interface driver ndiswrapper
kelly@Huntloom:~$ uname -rm
2.6.28-11-generic x86_64
kelly@Huntloom:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:53:6f:d4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.103 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:04:01.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a6:5a:21:36:20:6f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
kelly@Huntloom:~$ ndiswrapper -l
net8185 : driver installed
    device (10EC:8185) present (alternate driver: rtl8180)

```

BTW, I found these instructions, but couldn't execute them because I lack the knowhow: [http://ubuntuforums.org/showthread.php?t=968468](http://ubuntuforums.org/showthread.php?t=968468)

As far as I get it, your commands did basically the same, except that you used Win2000 or WinXP drivers.

---

### Post by pytheas22 on 2009-08-25
**hathiphnath**: the problem is that I had you load 32-bit Windows drivers into ndiswrapper, but you're running 64-bit Ubuntu (I assumed you were on 32-bit but I was wrong).  This won't work; you need 64-bit Windows drivers if you want to use 64-bit Linux and ndiswrapper.

Unfortunately, I did some searching and can't seem to find 64-bit Windows drivers for this device.  If you have any idea where you might download some, we could make this work.  Otherwise your only option would be to switch to 32-bit Ubuntu.

---

### Post by hathiphnath on 2009-08-25
I didn't even know that the bit version mattered to drivers. :)

The official drivers are here: [http://www.trendnet.com/downloads/list_subcategory.asp?SUBTYPE_ID=1061](http://www.trendnet.com/downloads/list_subcategory.asp?SUBTYPE_ID=1061)

The CD that came with the card has only one folder for WinXP (I'm assuming 32) and then has folders Vistax64 and Vistax86.

---

### Post by pytheas22 on 2009-08-25
Thanks for that link.  To install the 64-bit driver, download the "Driver/Utility XP 64-bit" and save to your desktop.  Then run:
```

sudo ndiswrapper -r net8185
cd ~/Desktop
unzip driver_utility_tew-421pc_423pi_winx64.zip 
sudo ndiswrapper -i WinX64/net8185x64.inf
```

Then reboot, and hopefully this will do it.  If it still doesn't work, please post:
```

ndiswrapper -l
dmesg | grep -e ndis -e wlan
sudo iwlist scan
```

---

### Post by hathiphnath on 2009-08-25
Won't boot up. :(

```
Starting kernel log daemon... 

[79.460499] BUG: soft lockup - CPU#1 stuck for 61s! [wrapndis_wq:1553]
```

All I did differently from usual was to use "sudo reboot" as I was already in the terminal and on the first bootup I had to reset the computer as it froze (or at least it seemed like that).

Edit: I tried to boot up from the liveCD and remove the driver, but of course, liveCD commands affect the liveCD environment. :(

---

### Post by pytheas22 on 2009-08-25
Sorry about that--there must be a serious disagreement between ndiswrapper and the 64-bit Windows driver to cause this.

You can fix the problem from the live CD by mounting your Ubuntu partition by selecting it from the "Places" menu in the live environment.  Then navigate to ...lib/modules/**2.6.xx-xx**/kernel/ubuntu/ndiswrapper and delete the file "ndiswrapper.ko."  (Replace the part in bold as appropriate, and note that if you have more than one kernel installed on your system, you will need to repeat this procedure to remove the ndiswrapper.ko file associated with each one of them.  Also note that you should be working with the file system mounted off your hard disk, note the live file system, so the full path to the location will be something like /media/disk/lib/modules/**2.6.xx-xx**/kernel/ubuntu/ndiswrapper--it will **not** be just /lib/modules/**2.6.xx-xx**/kernel/ubuntu/ndiswrapper.)

As for solving the original problem, I'm not sure what else you can do, unless you want to switch to 32-bit Ubuntu and use ndiswrapper there (I'm pretty sure that should work better, based on what I've read).  You could also try compiling the native Linux driver using the latest code; to do that, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2." Save it to your desktop. Then run these commands:

```
sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make
sudo make unload
sudo make load
sudo make install
```

Also open the blacklist file by typing 'sudo gedit /etc/modprobe.d/blacklist.conf' and remove the last three lines, which should involve the rtlxxxx modules.  After that reboot to begin using the new module.  I can't guarantee it will solve your wireless stability problems, but it shouldn't hurt.

---

### Post by Topher88 on 2009-08-25
> : I couldn't find Windows drivers for your card (but I didn't have time to search exhaustively). If you could please provide a link to the .exe or .zip file that you used to install drivers for your card in Windows, we can give ndiswrapper a try. I'm not sure it will work, but it's the only other option on your wireless card besides the 'wl' driver, which is a proprietary driver from Broadcom (and therefore difficult to fix without waiting Broadcom's help).
 
Hmmm... I didn't actually install any drivers: it's a laptop, so everything was ready to go out of the box. I'm sure I can find the specific drivers I'm using, though, if that's what I need to do.
 
I believe that I'm already using the Broadcom propriety driver in Linux, which I suspect is part of the culprit.

---

### Post by hathiphnath on 2009-08-25
Huh! It recovered! :)

But will it be okay to compile this under my 32-bit jaunty machine or does the build mean "custom build for this particular setup"?

The 64-bit has no wired connection whatsoever, so, I'd have to lug it around the house to install the builder tool... :)

Also, is this new built driver "generic", meaning it would work with Broadcom, etc? And in case I want to remove that new one, how would it work?

---

### Post by thirdI on 2009-08-25
Please help me out [COLOR=Black]pytheas; I have searched all over the boards for a solution to my wireless connection problems and after reading through this thread and realizing that I'm not the only one with this problem (very flaky), I believe you can help me out. I have listed all the output from the terminal commands...

lspci -nn:
[/COLOR]```
00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 01)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
01:06.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
01:09.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
```lsusb:```

Bus 001 Device 004: ID 0930:6545 Toshiba Corp. 
Bus 001 Device 002: ID 0ecd:a100 Lite-On IT Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:3200 Dell Computer Corp. Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```lshw -C Network:
```
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:66:03:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:30:bd:92:9b:36
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.8 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: pan0
       serial: 2a:85:4a:2b:0b:98
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```uname -rm:
```
2.6.28-15-generic i686
```iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"NETGEAR-2.4-G"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:3F:15:10:F3   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry limit:999999   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=50/100  Signal level:-75 dBm  Noise level=-69 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```dmesg | grep -e iwl -e wlan:
```
[   30.770498] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.292132] wlan0: direct probe to AP 00:e0:98:d3:05:ff try 1
[   32.294290] wlan0 direct probe responded
[   32.294295] wlan0: authenticate with AP 00:e0:98:d3:05:ff
[   32.313231] wlan0: authenticated
[   32.313240] wlan0: associate with AP 00:e0:98:d3:05:ff
[   32.331109] wlan0: RX AssocResp from 00:e0:98:d3:05:ff (capab=0x461 status=0 aid=1)
[   32.331114] wlan0: associated
[   32.331854] wlan0: disassociating by local choice (reason=3)
[  895.771764] wlan0: deauthenticated
[35355.660100] wlan0: authenticate with AP 00:18:01:ff:a5:9d
[35355.661540] wlan0: authenticated
[35355.661546] wlan0: associate with AP 00:18:01:ff:a5:9d
[35355.706816] wlan0: RX AssocResp from 00:18:01:ff:a5:9d (capab=0x431 status=0 aid=1)
[35355.706820] wlan0: associated
[35355.710049] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[35366.640050] wlan0: no IPv6 routers present
[35536.168032] wlan0: No ProbeResp from current AP 00:18:01:ff:a5:9d - assume out of range
[35537.766720] wlan0: direct probe to AP 00:18:01:ff:a5:9d try 1
[35537.964258] wlan0: direct probe to AP 00:18:01:ff:a5:9d try 2
[35538.164027] wlan0: direct probe to AP 00:18:01:ff:a5:9d try 3
[35538.364024] wlan0: direct probe to AP 00:18:01:ff:a5:9d timed out
[35554.988075] wlan0: authenticate with AP 00:e0:98:d3:05:ff
[35554.989456] wlan0: authenticated
[35554.989460] wlan0: associate with AP 00:e0:98:d3:05:ff
[35554.994780] wlan0: RX AssocResp from 00:e0:98:d3:05:ff (capab=0x461 status=0 aid=2)
[35554.994785] wlan0: associated
[35616.156486] wlan0 direct probe responded
[35616.156495] wlan0: authenticate with AP 00:e0:98:d3:05:ff
[35616.158334] wlan0: authenticated
[35616.158338] wlan0: associate with AP 00:e0:98:d3:05:ff
[35616.163992] wlan0: RX ReassocResp from 00:e0:98:d3:05:ff (capab=0x461 status=0 aid=2)
[35616.163995] wlan0: associated
[41729.817436] wlan0: authenticate with AP 00:e0:98:d3:05:ff
[41729.823780] wlan0: authenticated
[41729.823787] wlan0: associate with AP 00:e0:98:d3:05:ff
[41729.830819] wlan0: RX AssocResp from 00:e0:98:d3:05:ff (capab=0x461 status=0 aid=2)
[41729.830823] wlan0: associated
[41730.716307] wlan0: disassociating by local choice (reason=3)
[41767.008183] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[41767.009336] wlan0: direct probe to AP 00:22:3f:15:10:f3 try 1
[41767.012335] wlan0 direct probe responded
[41767.012341] wlan0: authenticate with AP 00:22:3f:15:10:f3
[41767.017839] wlan0: authenticated
[41767.017843] wlan0: associate with AP 00:22:3f:15:10:f3
[41767.046249] wlan0: RX AssocResp from 00:22:3f:15:10:f3 (capab=0x401 status=0 aid=1)
[41767.046252] wlan0: associated
[41767.046403] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[41770.802125] wlan0: authenticate with AP 00:22:3f:15:10:f3
[41770.802214] wlan0: authenticate with AP 00:22:3f:15:10:f3
[41770.827867] wlan0: authenticated
[41770.827875] wlan0: associate with AP 00:22:3f:15:10:f3
[41770.987944] wlan0: RX ReassocResp from 00:22:3f:15:10:f3 (capab=0x401 status=0 aid=1)
[41770.987949] wlan0: associated
[41777.116009] wlan0: no IPv6 routers present
[42932.505682] wlan0: deauthenticated
[42933.508052] wlan0: direct probe to AP 00:22:3f:15:10:f3 try 1
[42933.708039] wlan0: direct probe to AP 00:22:3f:15:10:f3 try 2
[42933.908030] wlan0: direct probe to AP 00:22:3f:15:10:f3 try 3
[42934.108055] wlan0: direct probe to AP 00:22:3f:15:10:f3 timed out
[42935.664528] wlan0: direct probe to AP 00:22:3f:15:10:f3 try 1
[42935.664571] wlan0: direct probe to AP 00:22:3f:15:10:f3 try 1
[42935.864833] wlan0: direct probe to AP 00:22:3f:15:10:f3 try 2
[42936.064037] wlan0: direct probe to AP 00:22:3f:15:10:f3 try 3
[42936.264027] wlan0: direct probe to AP 00:22:3f:15:10:f3 timed out
[42947.188473] wlan0: direct probe to AP 00:22:3f:15:10:f3 try 1
[42947.188520] wlan0: direct probe to AP 00:22:3f:15:10:f3 try 1
[42947.388032] wlan0: direct probe to AP 00:22:3f:15:10:f3 try 2
[42947.588893] wlan0: direct probe to AP 00:22:3f:15:10:f3 try 3
[42947.788355] wlan0: direct probe to AP 00:22:3f:15:10:f3 timed out
[42948.402004] wlan0: direct probe to AP 00:22:3f:15:10:f3 try 1
[42948.600223] wlan0: direct probe to AP 00:22:3f:15:10:f3 try 2
[42948.801025] wlan0: direct probe to AP 00:22:3f:15:10:f3 try 3
[42949.000179] wlan0: direct probe to AP 00:22:3f:15:10:f3 timed out
[42950.797023] wlan0: direct probe to AP 00:22:3f:15:10:f3 try 1
[42962.927915] wlan0: authenticate with AP 00:e0:98:d3:05:ff
[42962.931332] wlan0: authenticated
[42962.931337] wlan0: associate with AP 00:e0:98:d3:05:ff
[42962.943550] wlan0: RX AssocResp from 00:e0:98:d3:05:ff (capab=0x461 status=0 aid=2)
[42962.943555] wlan0: associated
[43024.941625] wlan0 direct probe responded
[43024.941633] wlan0: authenticate with AP 00:e0:98:d3:05:ff
[43024.943401] wlan0: authenticated
[43024.943408] wlan0: associate with AP 00:e0:98:d3:05:ff
[43024.946676] wlan0: RX ReassocResp from 00:e0:98:d3:05:ff (capab=0x461 status=0 aid=2)
[43024.946680] wlan0: associated
```cat /etc/issue:
```
Ubuntu 9.04 \n \l
```sudo iwlist scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:18:01:FF:A5:9D
                    ESSID:"PN3V7"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/100  Signal level:-76 dBm  Noise level=-71 dBm
                    Encryption key:on
                    IE: Unknown: 0005504E335637
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F010100200000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000010a0a7e8181
                    Extra: Last beacon: 1264ms ago
          Cell 02 - Address: 00:1F:90:EB:F1:24
                    ESSID:"2H632"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/100  Signal level:-79 dBm  Noise level=-71 dBm
                    Encryption key:on
                    IE: Unknown: 00053248363332
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F010100200000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000010a0adf6181
                    Extra: Last beacon: 1276ms ago
          Cell 03 - Address: 00:1D:19:E2:D8:E5
                    ESSID:"BABK8"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/100  Signal level:-75 dBm  Noise level=-71 dBm
                    Encryption key:on
                    IE: Unknown: 00054241424B38
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000130ae57181
                    Extra: Last beacon: 1340ms ago
          Cell 04 - Address: 00:1F:90:E5:27:5C
                    ESSID:"E3LN0"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/100  Signal level:-82 dBm  Noise level=-71 dBm
                    Encryption key:on
                    IE: Unknown: 000545334C4E30
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F010100200000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000037cfb2181
                    Extra: Last beacon: 1512ms ago
          Cell 05 - Address: 00:1F:90:EA:ED:CF
                    ESSID:"W5EU1"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/100  Signal level:-79 dBm  Noise level=-71 dBm
                    Encryption key:on
                    IE: Unknown: 00055735455531
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F010100200000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000083ea5437
                    Extra: Last beacon: 1264ms ago
          Cell 06 - Address: 00:1F:90:E7:49:CC
                    ESSID:"9GE21"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=61/100  Signal level:-65 dBm  Noise level=-71 dBm
                    Encryption key:on
                    IE: Unknown: 00053947453231
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F010100200000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000010a0ad2e34a
                    Extra: Last beacon: 1284ms ago
          Cell 07 - Address: 00:18:01:EB:22:A0
                    ESSID:"D8WO1"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/100  Signal level:-72 dBm  Noise level=-71 dBm
                    Encryption key:on
                    IE: Unknown: 00054438574F31
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F010100200000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000010a0a5524fd
                    Extra: Last beacon: 1476ms ago
          Cell 08 - Address: 00:E0:98:D3:05:FF
                    ESSID:"04Z411316520"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/100  Signal level:-76 dBm  Noise level=-71 dBm
                    Encryption key:off
                    IE: Unknown: 000C30345A343131333136353230
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000f1437a6b8
                    Extra: Last beacon: 1104ms ago
          Cell 09 - Address: 00:22:3F:15:10:F3
                    ESSID:"NETGEAR-2.4-G"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/100  Signal level:-69 dBm  Noise level=-71 dBm
                    Encryption key:off
                    IE: Unknown: 000D4E4554474541522D322E342D47
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A00011010440001011041000100103B00010310470010952EFCEA1C398D9A3E0C51B51C7437AA1021000D4E4554474541522C20496E632E10230008574E44523333303010240008574E4452333330301042000230311054000800060050F204000110110008574E445233333030100800020084103C000103
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000010a0c2aa18c
                    Extra: Last beacon: 1016ms ago
          Cell 10 - Address: 00:1F:90:ED:44:FE
                    ESSID:"GZL62"
                    Mode:Master
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=50/100  Signal level:-75 dBm  Noise level=-71 dBm
                    Encryption key:on
                    IE: Unknown: 0005475A4C3632
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030108
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F010100200000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000008fe1de536a
                    Extra: Last beacon: 724ms ago
          Cell 11 - Address: 00:17:31:FB:22:D6
                    ESSID:"remigio"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/100  Signal level:-82 dBm  Noise level=-71 dBm
                    Encryption key:on
                    IE: Unknown: 000772656D6967696F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000010a09d7518e
                    Extra: Last beacon: 1548ms ago
          Cell 12 - Address: 00:21:63:22:0F:D4
                    ESSID:"QNJH9"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/100  Signal level:-79 dBm  Noise level=-71 dBm
                    Encryption key:on
                    IE: Unknown: 0005514E4A4839
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000010a09a21d13
                    Extra: Last beacon: 804ms ago

pan0      Interface doesn't support scanning.
```

---

### Post by pytheas22 on 2009-08-25
**Topher88**: yes, you already are using the proprietary Broadcom Linux driver.  There's also an open-source Broadcom driver called b43, formerly bcm43xx, but it won't support your particular model because it doesn't work with any of the Broadcom 802.11n chips yet.  This means your only other option is to try ndiswrapper.  If you can find links to drivers for your laptop, the Windows wireless drive for your card should be there someplace.

**hathiphnath**: when it recovered (by which I guess you mean it booted properly), did the wireless work?
> 
But will it be okay to compile this under my 32-bit jaunty machine or does the build mean "custom build for this particular setup"?

I think you might be confused (or I'm confused).  You can compile compat-wireless on either a 32-bit or 64-bit system; it doesn't matter.  If your system is currently 64-bit, try compiling compat-wireless on it following the instructions in my previous post, then reboot.  The point of compiling compat-wireless is that it will give you a more up-to-date version of the wireless driver than the one that comes default with Ubuntu; the newer version might have fewer stability problems.

If compiling compat-wireless doesn't solve the problem, then your only option is going to be to switch to 32-bit Ubuntu and use ndiswrapper (or live with a flaky wireless connection).  But try compat-wireless on 64-bit Ubuntu first just to see if that helps.
> 
The 64-bit has no wired connection whatsoever, so, I'd have to lug it around the house to install the builder tool...

Unfortunately that's the only easy way to do this.  You could technically compile compat-wireless without being online, but it's not worth the hassle.
> 
Also, is this new built driver "generic", meaning it would work with Broadcom, etc? And in case I want to remove that new one, how would it work?

compat-wireless includes all the modern wireless drivers used by Linux, so yes, it supports your chipset (which is Realtek) as well as Broadcom, Atheros, Intel, etc.  So you will actually be updating all the wireless drivers on your systems when you compile compat-wireless, but unless you have other wireless cards, the only driver you'll ever be using is rtl8187 (which is for Realtek wireless chipsets).

**thirdI**: the b43 driver (which you're using) should work well on the Broadcom 4306 chipset (which you have).  Are you far from your router?  That can cause the disassociations you're seeing.  They can also be caused by NetworkManager misbehaving, so it might help if you installed wicd; see post #19 for instructions on that.

If wicd doesn't help and you're not far from your router, please start a new thread and I'll respond there, as this one is already becoming hard to keep track of.

---

### Post by gb2k01 on 2009-08-25
pytheas22:

So far so good with the wireless, it seems to be a lot more stable now (wicd) seems to have done the trick, though I can always try the other solutions if there's any problem that crops up. I appreciate your going out of your way to help me with that, thank you very much!!!

---

### Post by bkratz on 2009-08-25
[quote=

**thirdI**: the b43 driver (which you're using) should work well on the Broadcom 4306 chipset (which you have).  Are you far from your router?  That can cause the disassociations you're seeing.  They can also be caused by NetworkManager misbehaving, so it might help if you installed wicd; see post #19 for instructions on that.

If wicd doesn't help and you're not far from your router, please start a new thread and I'll respond there, as this one is already becoming hard to keep track of.[/quote]


Thirdl, sorry to interrupt, but I notice that you "see" two wireless networks-one of which is the one you are trying to use and on called remigio--- both with about the same signal strength and both on channel 6. You might want to change yours to some other channel.

---

### Post by thirdI on 2009-08-25
> **bkratz said:**
> Thirdl, sorry to interrupt, but I notice that you "see" two wireless networks-one of which is the one you are trying to use and on called remigio--- both with about the same signal strength and both on channel 6. You might want to change yours to some other channel.
Thanks for pointing that out; I'm guessing that the network signals are interfering with each other since they're on the same channel. How do I change the network channels, though?

---

### Post by bkratz on 2009-08-25
> **thirdI said:**
> Thanks for pointing that out; I'm guessing that the network signals are interfering with each other since they're on the same channel. How do I change the network channels, though?


The address really depends on the type of router you have (manufacturer). Ofter the admin page is at address 192.168.0.1, but not always.  I am looking for a posting that explained well and will send it to you as soon as I find it.

---

### Post by bkratz on 2009-08-25
> **bkratz said:**
> The address really depends on the type of router you have (manufacturer). Ofter the admin page is at address 192.168.0.1, but not always.  I am looking for a posting that explained well and will send it to you as soon as I find it.


I couldn't find the posting I was looking for but here is a link to general information.

[http://compnetworking.about.com/od/homenetworking/ht/routerconfigure.htm](http://compnetworking.about.com/od/homenetworking/ht/routerconfigure.htm)

Good Luck!

---

### Post by pytheas22 on 2009-08-26
> Thirdl, sorry to interrupt, but I notice that you "see" two wireless networks-one of which is the one you are trying to use and on called remigio--- both with about the same signal strength and both on channel 6. You might want to change yours to some other channel.

This is a very good point.  I didn't look closely enough at your outputs to notice this, but high interference can also cause the kind of dropouts you're experiencing.

A quick way to find the address of your router is to go to System>Administration>Network Tools.  Click on the Netstat tab, and select the "Routing Table Information" option, then press the button.  The second column of the third row should be the address of your router.  As bkratz explained, just put that address in the address bar in Firefox and you should see your router's configuration page (if you're asked for a login, the default credentials are usually printed on the outside of the router somewhere).  You can use this interface to change channels.

---

### Post by hathiphnath on 2009-08-26
> **pytheas22 said:**
> **hathiphnath**: when it recovered (by which I guess you mean it booted properly), did the wireless work? If there was a difference between that state and the original state, it was that the newer disconnected more often. The weird thing was that the computer needed two reboots to actually find the network, and same thing (dual-reboot) was needed when I installed compat-wireless.

> **pytheas22 said:**
> I think you might be confused (or I'm confused).  You can compile compat-wireless on either a 32-bit or 64-bit system; it doesn't matter.I have another ubuntu setup (32-bit) that has a wired connection. I'd have added that too in my signature but it has a 250-character cap. :(

> **pytheas22 said:**
> If compiling compat-wireless doesn't solve the problem, then your only option is going to be to switch to 32-bit Ubuntu and use ndiswrapper (or live with a flaky wireless connection).  But try compat-wireless on 64-bit Ubuntu first just to see if that helps.Basically it didn't... the main difference between that and the original state was that the newer claimed signal strength to be mostly at 0% (even when right next to a wifi-router!) and my main computer (XP laptop) has no wireless issues (signal strength or otherwise) in the household.

> **pytheas22 said:**
> compat-wireless includes all the modern wireless drivers used by Linux, so yes, it supports your chipset (which is Realtek) as well as Broadcom, Atheros, Intel, etc.  So you will actually be updating all the wireless drivers on your systems when you compile compat-wireless, but unless you have other wireless cards, the only driver you'll ever be using is rtl8187 (which is for Realtek wireless chipsets).I also have Broadcom BCM4306 card in the other setup which doesn't currently use wireless (so, I'm unaware of its issues), but I'm hesitant to break the brand new (64-bit) box open to switch the cards as it might void the warranty.

---

### Post by pytheas22 on 2009-08-26
**hathiphnath**: I'm sorry the newer version of the driver only made things worse.

At this point, again, I don't think there's anything else you can do besides switch to 32-bit Ubuntu on your Trendnet box and use ndiswrapper, or wait for the native Linux driver to improve.

It's also possible that switching the settings of your wireless network could help--for example, try changing the channel and mode--but I don't think that's really the problem here.

---

### Post by hathiphnath on 2009-08-26
> **pytheas22 said:**
> At this point, again, I don't think there's anything else you can do besides switch to 32-bit Ubuntu on your Trendnet box and use ndiswrapper, or wait for the native Linux driver to improve.I did switch to 32 now and followed your initial instructions... It was all blazing fast near the router, but tends to disconnects in the room where it's supposed to be... I'll need to test in near the router again to see if it works flawlessly there... and if it does, I'll probably need to buy [_a directional antenna for the card_]("http://www.trendnet.com/products/proddetail.asp?prod=125_TEW-AI86DB&cat=68").

I'll be back to report how it went.

---

### Post by hathiphnath on 2009-08-26
> **hathiphnath said:**
> I'll be back to report how it went.
LOL! I just realised I left the "you'll not be hearing from me again in this thread" sign... or at least that's the impression I've had from "reporting back" when googling linux issues.

But in any case, now my Trendnet box works flawlessly in the router room and the one next to it... All I need now is a directional antenna to make it work where it's supposed to! So much for upgrading to 64! :P

Thanks a bunch, Pytheas! You were really invaluable in this! :guitar:

---

### Post by pytheas22 on 2009-08-26
**hathiphnath**: really glad to hear it worked out, and sorry to put you through so much before coming to the conclusion that 32-bit and ndiswrapper was the only way to go.  Hopefully the native Linux driver will improve soon so that you can switch back to 64-bit, but for now at least you'll have stable wireless.

---

### Post by thirdI on 2009-08-26
Switching channels did the trick, there's barely any interference with my wireless signal now! Thanks bkratz and pytheas for all your help.

---

### Post by Hende86 on 2010-10-12
> **rose34 said:**
> Hi everyone,

I have recently returned from university, bringing my computer with me. At uni, my ubuntu installation worked fine on our wireless network, but now I have it at home the connection seems very unstable. It will go from speeds of 100kbps - 4kbps, and frequently lose connection altogether. I have not changed anything on my computer since getting home, and is much closer to the router physically than the windows pc I am writing this on, which enjoys a constant speed of about 85kbps.

Does anyone have any suggestions as to what could be wrong?

Thanks!
Joe

I have the same problem! Should I post the following commands?

> **pytheas22 said:**
> I would suspect a problem with your wireless driver.  If you could please post the output of the following commands, I'll know which driver you're using, and can probably find an alternative that may work better:
```

lspci -nn
lsusb
lshw -C Network
uname -rm
iwconfig
```

Any help would be greatly appreciated.

-Hende

---

### Post by pytheas22 on 2010-10-12
**Hende**: yes, please post those commands so we can see what might be wrong.

---

### Post by Hende86 on 2010-10-12
lspci -nn:

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G86 [GeForce 8400M GS] [10de:0427] (rev a1)
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
07:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
07:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
07:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
07:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)

lsusb:

Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lshw -C Network:

*-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 61
       serial: 00:13:e8:a0:b9:d7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-22-generic firmware=228.61.2.24 ip=82.181.155.35 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:f4000000-f4001fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:24:97:32:53
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:45 ioport:c000(size=256) memory:f8000000-f8000fff memory:80000000-8001ffff

uname -rm:
2.6.35-22-generic i686

iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Maksy"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:22:15:87:99:5B   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Here they are.

---

### Post by pytheas22 on 2010-10-13
**Hende86**: hmmm, you have an Intel 4965 wireless card, which should work very well under the iwlagn module.

Your problem is that you're able to connect to one network without problems, but then suffer poor connectivity when you connect to a different network in a different location?  Have you checked on possible interference from other routers on the network that gives poor connectivity?

It wouldn't hurt also to see the output of:
```

dmesg | grep -e wlan -e iwl
sudo iwlist scan
```

---

### Post by Hende86 on 2010-10-13
55015 PROTO=UDP SPT=23013 DPT=6881 LEN=75 
[13638.362793] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=86.16.154.71 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=47 ID=15856 DF PROTO=TCP SPT=50820 DPT=6881 WINDOW=0 RES=0x00 RST URGP=0 
[13651.520900] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=205.250.104.174 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=104 ID=6618 PROTO=UDP SPT=61157 DPT=6881 LEN=75 
[13660.454347] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=217.164.60.72 DST=82.181.155.35 LEN=52 TOS=0x00 PREC=0x00 TTL=48 ID=41334 DF PROTO=TCP SPT=59349 DPT=6881 WINDOW=33304 RES=0x00 ACK FIN URGP=0 
[13674.510641] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=79.183.118.205 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=111 ID=31170 PROTO=UDP SPT=36337 DPT=6881 LEN=75 
[13690.319185] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=203.73.225.122 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=108 ID=19545 PROTO=UDP SPT=18222 DPT=6881 LEN=75 
[13710.172599] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=66.222.159.85 DST=82.181.155.35 LEN=58 TOS=0x00 PREC=0x00 TTL=107 ID=18590 PROTO=UDP SPT=54292 DPT=6881 LEN=38 
[13713.852404] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=201.86.27.232 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=236 ID=22602 PROTO=TCP SPT=27780 DPT=33734 WINDOW=0 RES=0x00 ACK RST URGP=0 
[13717.779824] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=189.29.130.128 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=8586 DF PROTO=TCP SPT=61301 DPT=34732 WINDOW=0 RES=0x00 ACK RST URGP=0 
[13720.112810] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=189.29.130.128 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=9003 DF PROTO=TCP SPT=61301 DPT=34732 WINDOW=0 RES=0x00 ACK RST URGP=0 
[13734.332900] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=94.70.25.215 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=115 ID=22428 PROTO=UDP SPT=10004 DPT=6881 LEN=75 
[13753.054944] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=67.161.160.61 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=43 ID=62001 DF PROTO=TCP SPT=57110 DPT=6881 WINDOW=0 RES=0x00 RST URGP=0 
[13753.154781] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=79.176.165.209 DST=82.181.155.35 LEN=58 TOS=0x00 PREC=0x00 TTL=111 ID=18773 PROTO=UDP SPT=36290 DPT=6881 LEN=38 
[13769.858441] iwlagn 0000:02:00.0: Microcode SW error detected.  Restarting 0x82000000.
[13769.858453] iwlagn 0000:02:00.0: Loaded firmware version: 228.61.2.24
[13769.858495] iwlagn 0000:02:00.0: Start IWL Error Log Dump:
[13769.858504] iwlagn 0000:02:00.0: Status: 0x000213E4, count: 5
[13769.858688] iwlagn 0000:02:00.0: Desc                               Time       data1      data2      line
[13769.858701] iwlagn 0000:02:00.0: FH_ERROR                     (#12) 3776529122 0x00000008 0x03530000 208
[13769.858710] iwlagn 0000:02:00.0: pc      blink1  blink2  ilink1  ilink2  hcmd
[13769.858721] iwlagn 0000:02:00.0: 0x0046C 0x0A332 0x004C2 0x006DE 0x0A36A 0x2EE001C
[13769.858729] iwlagn 0000:02:00.0: FH register values:
[13769.858771] iwlagn 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X03466600
[13769.858812] iwlagn 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X003403b0
[13769.858854] iwlagn 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000b0
[13769.858896] iwlagn 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00819004
[13769.858937] iwlagn 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X0000003c
[13769.858980] iwlagn 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X03530000
[13769.859021] iwlagn 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[13769.859063] iwlagn 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0002
[13769.859105] iwlagn 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[13769.859190] iwlagn 0000:02:00.0: Start IWL Event Log Dump: display last 20 entries
[13769.859237] iwlagn 0000:02:00.0: EVT_LOGT:3776528612:0x00000107:0106
[13769.859275] iwlagn 0000:02:00.0: EVT_LOGT:3776528614:0x00000000:0302
[13769.859313] iwlagn 0000:02:00.0: EVT_LOGT:3776528645:0x000000d4:0321
[13769.859351] iwlagn 0000:02:00.0: EVT_LOGT:3776528646:0x00000000:1350
[13769.859388] iwlagn 0000:02:00.0: EVT_LOGT:3776528647:0x00000000:1351
[13769.859425] iwlagn 0000:02:00.0: EVT_LOGT:3776528647:0x00000001:1352
[13769.859462] iwlagn 0000:02:00.0: EVT_LOGT:3776528648:0x00000003:1353
[13769.859500] iwlagn 0000:02:00.0: EVT_LOGT:3776528656:0x00000344:0357
[13769.859537] iwlagn 0000:02:00.0: EVT_LOGT:3776528810:0x02ee001c:0206
[13769.859573] iwlagn 0000:02:00.0: EVT_LOGT:3776528811:0x00000001:0204
[13769.859611] iwlagn 0000:02:00.0: EVT_LOGT:3776528815:0x00000001:0219
[13769.859647] iwlagn 0000:02:00.0: EVT_LOGT:3776528815:0x00000200:0211
[13769.859684] iwlagn 0000:02:00.0: EVT_LOGT:3776529012:0x00000000:0212
[13769.859721] iwlagn 0000:02:00.0: EVT_LOGT:3776529065:0x00000000:0215
[13769.859758] iwlagn 0000:02:00.0: EVT_LOGT:3776529067:0x00000008:0220
[13769.859795] iwlagn 0000:02:00.0: EVT_LOGT:3776529084:0x00000000:0302
[13769.859832] iwlagn 0000:02:00.0: EVT_LOGT:3776529113:0x000000d4:0303
[13769.859870] iwlagn 0000:02:00.0: EVT_LOGT:3776529117:0x00000eef:0217
[13769.859907] iwlagn 0000:02:00.0: EVT_LOGT:3776529117:0x02ee001c:0217
[13769.859944] iwlagn 0000:02:00.0: EVT_LOGT:3776529125:0x00000000:0125
[13771.134911] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=89.201.178.57 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=115 ID=55836 PROTO=UDP SPT=6356 DPT=6881 LEN=75 
[13797.310094] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=71.38.24.135 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=110 ID=50599 PROTO=UDP SPT=32294 DPT=6881 LEN=75 
[13804.576839] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=189.249.59.220 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=231 ID=15761 DF PROTO=TCP SPT=19575 DPT=51642 WINDOW=0 RES=0x00 ACK RST URGP=0 
[13805.310269] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=202.79.17.102 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=111 ID=33801 DF PROTO=TCP SPT=3228 DPT=6881 WINDOW=0 RES=0x00 ACK RST URGP=0 
[13811.242531] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=66.222.159.85 DST=82.181.155.35 LEN=58 TOS=0x00 PREC=0x00 TTL=107 ID=35934 PROTO=UDP SPT=54292 DPT=6881 LEN=38 
[13814.218097] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=77.125.79.4 DST=82.181.155.35 LEN=120 TOS=0x00 PREC=0x00 TTL=40 ID=63197 DF PROTO=TCP SPT=64821 DPT=6881 WINDOW=33026 RES=0x00 ACK PSH FIN URGP=0 
[13819.030374] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=201.86.27.232 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=236 ID=22811 PROTO=TCP SPT=27978 DPT=41637 WINDOW=0 RES=0x00 ACK RST URGP=0 
[13831.984288] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=62.194.88.35 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=116 ID=19676 PROTO=UDP SPT=57848 DPT=6881 LEN=75 
[13855.199745] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=80.184.24.138 DST=82.181.155.35 LEN=58 TOS=0x00 PREC=0x00 TTL=112 ID=15160 PROTO=UDP SPT=20182 DPT=6881 LEN=38 
[13861.648567] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=121.216.221.195 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=231 ID=62892 DF PROTO=TCP SPT=14036 DPT=52614 WINDOW=0 RES=0x00 ACK RST URGP=0 
[13871.326422] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=66.222.159.85 DST=82.181.155.35 LEN=58 TOS=0x00 PREC=0x00 TTL=107 ID=46353 PROTO=UDP SPT=54292 DPT=6881 LEN=38 
[13892.349794] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=68.207.100.18 DST=82.181.155.35 LEN=58 TOS=0x00 PREC=0x00 TTL=108 ID=15975 PROTO=UDP SPT=61000 DPT=6881 LEN=38 
[13892.428272] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=189.29.130.128 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=108 ID=26243 DF PROTO=TCP SPT=61934 DPT=38966 WINDOW=0 RES=0x00 ACK RST URGP=0 
[13893.153279] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=189.38.177.104 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=43 ID=0 DF PROTO=TCP SPT=51413 DPT=44189 WINDOW=0 RES=0x00 RST URGP=0 
[13910.579874] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=174.116.75.156 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=109 ID=12776 PROTO=UDP SPT=25287 DPT=6881 LEN=75 
[13917.846397] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=121.216.221.195 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=231 ID=23569 DF PROTO=TCP SPT=14036 DPT=53105 WINDOW=0 RES=0x00 ACK RST URGP=0 
[13919.968155] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=200.82.218.93 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=48 ID=58400 DF PROTO=TCP SPT=31913 DPT=47348 WINDOW=0 RES=0x00 RST URGP=0 
[13931.116567] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=89.249.211.155 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=107 ID=666 PROTO=UDP SPT=10293 DPT=6881 LEN=75 
[18007.406340] iwlagn 0000:02:00.0: ACTIVATE a non DRIVER active station id 0 addr 00:22:15:87:99:5b
[18007.420196] wlan0: deauthenticating from 00:22:15:87:99:5b by local choice (reason=3)
[18012.625467] iwlagn 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[18012.625535] iwlagn 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf4000004)
[18012.625566] iwlagn 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[18012.625596] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[18012.627651] iwlagn 0000:02:00.0: RF_KILL bit toggled to enable radio.
[18016.252676] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[18021.027262] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18021.029218] wlan0: authenticated
[18021.029294] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18021.031774] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18021.031782] wlan0: associated
[18021.059736] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[18024.983164] wlan0: deauthenticated from 00:22:15:87:99:5b (Reason: 15)
[18027.310641] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18027.313521] wlan0: authenticated
[18027.313570] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18027.316097] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18027.316105] wlan0: associated
[18031.283685] wlan0: deauthenticated from 00:22:15:87:99:5b (Reason: 15)
[18031.808050] wlan0: no IPv6 routers present
[18033.740377] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18033.742279] wlan0: authenticated
[18033.742338] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18033.744828] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18033.744836] wlan0: associated
[18037.684228] wlan0: deauthenticated from 00:22:15:87:99:5b (Reason: 15)
[18040.038571] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18040.042175] wlan0: authenticated
[18040.042227] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18040.045789] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18040.045793] wlan0: associated
[18043.985884] wlan0: deauthenticated from 00:22:15:87:99:5b (Reason: 15)
[18046.420946] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18046.423733] wlan0: authenticated
[18046.423784] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18046.426234] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18046.426242] wlan0: associated
[18050.385211] wlan0: deauthenticated from 00:22:15:87:99:5b (Reason: 15)
[18052.736780] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18052.741016] wlan0: authenticated
[18052.741067] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18052.743548] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18052.743557] wlan0: associated
[18056.686570] wlan0: deauthenticated from 00:22:15:87:99:5b (Reason: 15)
[18059.118284] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18059.120144] wlan0: authenticated
[18059.120192] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18059.122626] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18059.122635] wlan0: associated
[18063.086288] wlan0: deauthenticated from 00:22:15:87:99:5b (Reason: 15)
[18065.392242] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18065.394151] wlan0: authenticated
[18065.394202] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18065.396728] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18065.396736] wlan0: associated
[18069.386788] wlan0: deauthenticated from 00:22:15:87:99:5b (Reason: 15)
[18071.818179] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18071.820111] wlan0: authenticated
[18071.820162] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18071.822651] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18071.822659] wlan0: associated
[18078.824096] wlan0: deauthenticating from 00:22:15:87:99:5b by local choice (reason=3)
[18156.047585] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18156.244121] wlan0: authenticate with 00:22:15:87:99:5b (try 2)
[18156.444116] wlan0: authenticate with 00:22:15:87:99:5b (try 3)
[18156.644110] wlan0: authentication with 00:22:15:87:99:5b timed out
[18168.269286] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18168.271189] wlan0: authenticated
[18168.271243] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18168.274901] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18168.274910] wlan0: associated
[18172.195132] wlan0: deauthenticated from 00:22:15:87:99:5b (Reason: 15)
[18174.605907] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18174.607831] wlan0: authenticated
[18174.607881] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18174.610336] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18174.610345] wlan0: associated
[18178.595653] wlan0: deauthenticated from 00:22:15:87:99:5b (Reason: 15)
[18181.017349] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18181.019279] wlan0: authenticated
[18181.019329] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18181.021763] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18181.021771] wlan0: associated
[18184.996162] wlan0: deauthenticated from 00:22:15:87:99:5b (Reason: 15)
[18205.619667] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18205.623649] wlan0: authenticated
[18205.623700] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18205.632093] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18205.632101] wlan0: associated
[18215.676186] wlan0: deauthenticating from 00:22:15:87:99:5b by local choice (reason=3)
[18217.939080] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18218.136058] wlan0: authenticate with 00:22:15:87:99:5b (try 2)
[18218.336142] wlan0: authenticate with 00:22:15:87:99:5b (try 3)
[18218.536057] wlan0: authentication with 00:22:15:87:99:5b timed out
[18230.302092] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18230.303992] wlan0: authenticated
[18230.304044] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18230.306497] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18230.306506] wlan0: associated
[18234.300153] wlan0: deauthenticated from 00:22:15:87:99:5b (Reason: 15)
[18236.653575] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18236.655467] wlan0: authenticated
[18236.655519] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18236.658019] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18236.658028] wlan0: associated
[18240.600687] wlan0: deauthenticated from 00:22:15:87:99:5b (Reason: 15)
[18243.032169] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18243.034089] wlan0: authenticated
[18243.034140] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18243.036610] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18243.036618] wlan0: associated
[18247.001217] wlan0: deauthenticated from 00:22:15:87:99:5b (Reason: 15)
[18249.359451] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18249.372223] wlan0: authenticated
[18249.372258] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18249.390423] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18249.390427] wlan0: associated
[18253.303277] wlan0: deauthenticated from 00:22:15:87:99:5b (Reason: 15)
[18255.729765] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18255.731769] wlan0: authenticated
[18255.731827] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18255.734368] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18255.734376] wlan0: associated
[18259.702289] wlan0: deauthenticated from 00:22:15:87:99:5b (Reason: 15)
[18262.104870] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18262.108058] wlan0: authenticated
[18262.108108] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18262.122766] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18262.122770] wlan0: associated
[18263.821082] wlan0: deauthenticating from 00:22:15:87:99:5b by local choice (reason=3)
[18274.864091] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18274.873668] wlan0: authenticated
[18274.873692] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18274.889223] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18274.889227] wlan0: associated
[18278.804978] wlan0: deauthenticated from 00:22:15:87:99:5b (Reason: 15)
[18281.184982] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18281.186884] wlan0: authenticated
[18281.186936] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18281.189412] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18281.189420] wlan0: associated
[18291.234389] wlan0: deauthenticating from 00:22:15:87:99:5b by local choice (reason=3)
[18293.532757] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18293.732105] wlan0: authenticate with 00:22:15:87:99:5b (try 2)
[18293.932104] wlan0: authenticate with 00:22:15:87:99:5b (try 3)
[18294.132121] wlan0: authentication with 00:22:15:87:99:5b timed out
[18313.093704] wlan0: authenticate with 00:22:15:87:99:5b (try 1)
[18313.095672] wlan0: authenticated
[18313.095723] wlan0: associate with 00:22:15:87:99:5b (try 1)
[18313.098165] wlan0: RX AssocResp from 00:22:15:87:99:5b (capab=0x411 status=0 aid=1)
[18313.098174] wlan0: associated
[18383.123075] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=89.77.69.58 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=111 ID=1651 PROTO=UDP SPT=52673 DPT=6881 LEN=75 
[18383.140413] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=89.77.69.58 DST=82.181.155.35 LEN=58 TOS=0x00 PREC=0x00 TTL=111 ID=1664 PROTO=UDP SPT=52673 DPT=6881 LEN=38 
[18383.519234] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=142.161.99.99 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=109 ID=17612 PROTO=UDP SPT=4838 DPT=6881 LEN=75 
[18384.021021] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=60.242.198.93 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=114 ID=45469 PROTO=UDP SPT=30331 DPT=6881 LEN=75 
[18384.198638] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=110.174.241.99 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=113 ID=10883 PROTO=UDP SPT=37970 DPT=6881 LEN=75 
[18385.775482] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=94.98.133.84 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=110 ID=4271 PROTO=UDP SPT=28513 DPT=6881 LEN=75 
[18386.153398] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=89.77.69.58 DST=82.181.155.35 LEN=58 TOS=0x00 PREC=0x00 TTL=111 ID=1865 PROTO=UDP SPT=52673 DPT=6881 LEN=38 
[18387.328547] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=119.157.118.154 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=110 ID=34017 PROTO=UDP SPT=45682 DPT=6881 LEN=75 
[18388.164835] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=90.191.166.23 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=115 ID=15551 PROTO=UDP SPT=61408 DPT=6881 LEN=75 
[18388.178467] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=83.24.223.93 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=115 ID=59452 PROTO=UDP SPT=12053 DPT=6881 LEN=75 
[18403.145521] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=124.187.235.251 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=101 ID=27494 PROTO=UDP SPT=54535 DPT=6881 LEN=75 
[18405.436429] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=194.152.46.2 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=50245 DPT=6881 WINDOW=0 RES=0x00 RST URGP=0 
[18405.450721] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=194.152.46.2 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=50245 DPT=6881 WINDOW=0 RES=0x00 RST URGP=0 
[18405.459036] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=194.152.46.2 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=50245 DPT=6881 WINDOW=0 RES=0x00 RST URGP=0 
[18405.486251] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=194.152.46.2 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=50245 DPT=6881 WINDOW=0 RES=0x00 RST URGP=0 
[18405.509647] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=194.152.46.2 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=50245 DPT=6881 WINDOW=0 RES=0x00 RST URGP=0 
[18405.524378] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=194.152.46.2 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=50245 DPT=6881 WINDOW=0 RES=0x00 RST URGP=0 
[18405.534150] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=194.152.46.2 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=50245 DPT=6881 WINDOW=0 RES=0x00 RST URGP=0 
[18405.544161] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=194.152.46.2 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=50245 DPT=6881 WINDOW=0 RES=0x00 RST URGP=0 
[18405.570356] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=194.152.46.2 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=50245 DPT=6881 WINDOW=0 RES=0x00 RST URGP=0 
[18405.576350] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=194.152.46.2 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=50245 DPT=6881 WINDOW=0 RES=0x00 RST URGP=0 
[18423.593867] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=201.52.102.89 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=112 ID=19858 PROTO=UDP SPT=61982 DPT=6881 LEN=75 
[18426.447954] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=189.27.11.213 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=237 ID=38332 PROTO=TCP SPT=16753 DPT=43328 WINDOW=0 RES=0x00 ACK RST URGP=0 
[18443.376974] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=83.132.191.214 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=112 ID=7399 PROTO=UDP SPT=48422 DPT=6881 LEN=75 
[18451.378254] iwlagn 0000:02:00.0: Microcode SW error detected.  Restarting 0x82000000.
[18451.378266] iwlagn 0000:02:00.0: Loaded firmware version: 228.61.2.24
[18451.378288] iwlagn 0000:02:00.0: Start IWL Error Log Dump:
[18451.378297] iwlagn 0000:02:00.0: Status: 0x000213E4, count: 5
[18451.378461] iwlagn 0000:02:00.0: Desc                               Time       data1      data2      line
[18451.378474] iwlagn 0000:02:00.0: FH_ERROR                     (#12) 0000160000 0x00000008 0x03130000 208
[18451.378483] iwlagn 0000:02:00.0: pc      blink1  blink2  ilink1  ilink2  hcmd
[18451.378494] iwlagn 0000:02:00.0: 0x0046C 0x05CB2 0x004C2 0x006DA 0x018B8 0x4C5004E
[18451.378502] iwlagn 0000:02:00.0: FH register values:
[18451.378524] iwlagn 0000:02:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X03466600
[18451.378545] iwlagn 0000:02:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X003403b0
[18451.378567] iwlagn 0000:02:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000020
[18451.378589] iwlagn 0000:02:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X00819004
[18451.378610] iwlagn 0000:02:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X0000003c
[18451.378632] iwlagn 0000:02:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X03130000
[18451.378653] iwlagn 0000:02:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[18451.378675] iwlagn 0000:02:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0002
[18451.378696] iwlagn 0000:02:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[18451.378761] iwlagn 0000:02:00.0: Start IWL Event Log Dump: display last 20 entries
[18451.378787] iwlagn 0000:02:00.0: EVT_LOGT:0000158628:0x00000000:1351
[18451.378804] iwlagn 0000:02:00.0: EVT_LOGT:0000158628:0x00000000:1352
[18451.378820] iwlagn 0000:02:00.0: EVT_LOGT:0000158629:0x00000003:1353
[18451.378837] iwlagn 0000:02:00.0: EVT_LOGT:0000158637:0x000000f8:0357
[18451.378854] iwlagn 0000:02:00.0: EVT_LOGT:0000159185:0x00000107:0106
[18451.378870] iwlagn 0000:02:00.0: EVT_LOGT:0000159186:0x00000000:0302
[18451.378887] iwlagn 0000:02:00.0: EVT_LOGT:0000159222:0x000000d4:0321
[18451.378904] iwlagn 0000:02:00.0: EVT_LOGT:0000159223:0x00000000:1350
[18451.378920] iwlagn 0000:02:00.0: EVT_LOGT:0000159223:0x00000000:1351
[18451.378937] iwlagn 0000:02:00.0: EVT_LOGT:0000159224:0x00000000:1352
[18451.378953] iwlagn 0000:02:00.0: EVT_LOGT:0000159224:0x00000003:1353
[18451.378970] iwlagn 0000:02:00.0: EVT_LOGT:0000159232:0x000000f9:0357
[18451.378987] iwlagn 0000:02:00.0: EVT_LOGT:0000159934:0x00000107:0106
[18451.379003] iwlagn 0000:02:00.0: EVT_LOGT:0000159935:0x00000000:0302
[18451.379020] iwlagn 0000:02:00.0: EVT_LOGT:0000159982:0x000000d4:0321
[18451.379036] iwlagn 0000:02:00.0: EVT_LOGT:0000159983:0x00000000:1350
[18451.379053] iwlagn 0000:02:00.0: EVT_LOGT:0000159984:0x00000000:1351
[18451.379069] iwlagn 0000:02:00.0: EVT_LOGT:0000159984:0x00000000:1352
[18451.379085] iwlagn 0000:02:00.0: EVT_LOGT:0000159985:0x00000003:1353
[18451.379102] iwlagn 0000:02:00.0: EVT_LOGT:0000160003:0x00000000:0125
[18454.825073] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=121.7.242.239 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=230 ID=30727 DF PROTO=TCP SPT=19580 DPT=49152 WINDOW=0 RES=0x00 ACK RST URGP=0 
[18463.612004] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=24.235.223.228 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=113 ID=24195 PROTO=UDP SPT=28970 DPT=6881 LEN=75 
[18468.950169] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=213.171.132.58 DST=82.181.155.35 LEN=52 TOS=0x00 PREC=0x00 TTL=52 ID=46064 DF PROTO=TCP SPT=27732 DPT=6881 WINDOW=8208 RES=0x00 ACK FIN URGP=0 
[18483.146374] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=66.222.159.85 DST=82.181.155.35 LEN=58 TOS=0x00 PREC=0x00 TTL=107 ID=2945 PROTO=UDP SPT=54292 DPT=6881 LEN=38 
[18488.933471] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=86.171.149.137 DST=82.181.155.35 LEN=52 TOS=0x00 PREC=0x00 TTL=43 ID=28668 DF PROTO=TCP SPT=52705 DPT=48920 WINDOW=65535 RES=0x00 ACK URGP=0 
[18503.444147] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=68.173.176.247 DST=82.181.155.35 LEN=58 TOS=0x00 PREC=0x00 TTL=113 ID=38091 PROTO=UDP SPT=40793 DPT=6881 LEN=38 
[18505.778623] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=86.171.149.137 DST=82.181.155.35 LEN=52 TOS=0x00 PREC=0x00 TTL=43 ID=65232 PROTO=TCP SPT=52705 DPT=48920 WINDOW=65535 RES=0x00 ACK URGP=0 
[18527.321029] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=203.15.140.24 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=106 ID=7676 PROTO=UDP SPT=1579 DPT=6881 LEN=75 
[18529.214169] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=189.27.11.213 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=237 ID=38643 PROTO=TCP SPT=17037 DPT=44128 WINDOW=0 RES=0x00 ACK RST URGP=0 
[18543.133529] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=207.204.131.254 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=101 ID=15968 PROTO=UDP SPT=63051 DPT=6881 LEN=75 
[18545.443087] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=194.152.46.2 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=50245 DPT=6881 WINDOW=0 RES=0x00 RST URGP=0 
[18565.203738] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=218.212.162.46 DST=82.181.155.35 LEN=48 TOS=0x00 PREC=0x00 TTL=43 ID=6492 DF PROTO=TCP SPT=54579 DPT=49881 WINDOW=65535 RES=0x00 SYN URGP=0 
[18566.499260] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=194.152.46.2 DST=82.181.155.35 LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=TCP SPT=50245 DPT=6881 WINDOW=0 RES=0x00 RST URGP=0 
[18587.554353] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=76.229.163.174 DST=82.181.155.35 LEN=58 TOS=0x00 PREC=0x00 TTL=111 ID=43381 PROTO=UDP SPT=49899 DPT=6881 LEN=38 
[18603.568044] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=78.169.9.2 DST=82.181.155.35 LEN=95 TOS=0x00 PREC=0x00 TTL=115 ID=12984 PROTO=UDP SPT=13412 DPT=6881 LEN=75 
[18603.580823] [UFW BLOCK] IN=wlan0 OUT= 
dmesg | grep -e wlan -e iwl:

MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=86.171.149.137 DST=82.181.155.35 LEN=52 TOS=0x00 PREC=0x00 TTL=43 ID=35160 PROTO=TCP SPT=52705 DPT=48920 WINDOW=65535 RES=0x00 ACK URGP=0 
[18606.193352] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=220.231.91.90 DST=82.181.155.35 LEN=52 TOS=0x00 PREC=0x00 TTL=43 ID=64944 DF PROTO=TCP SPT=19543 DPT=6881 WINDOW=33304 RES=0x00 ACK FIN URGP=0 
[18623.178297] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=87.10.182.221 DST=82.181.155.35 LEN=58 TOS=0x00 PREC=0x00 TTL=110 ID=31819 PROTO=UDP SPT=25754 DPT=6881 LEN=38 
[18632.645544] [UFW BLOCK] IN=wlan0 OUT= MAC=00:13:e8:a0:b9:d7:00:13:5f:01:92:a1:08:00 SRC=88.243.51.218 DST=82.181.155.35 LEN=52 TOS=0x00 PREC=0x00 TTL=50 ID=38477 DF PROTO=TCP SPT=47464 DPT=6881 WINDOW=92 RES=0x00 ACK FIN URGP=0 

sudo iwlist scan:

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable

Here is the outputs....

The problem is the wireless connection is very unstable at home. I haven't tried it anywhere else. The thing is that my wlan works very well when I reboot my wireless box but drops off on average after one hour or so and then I have to reboot the box again to find the connection.

---

### Post by pytheas22 on 2010-10-13
Thanks for the output.  I see from dmesg that there is indeed something going wrong with the wireless card.  It looks from lines like this that there may be an issue with the firmware:
```

[18451.378254] iwlagn 0000:02:00.0: Microcode SW error detected. Restarting 0x82000000.
```

You might have better luck if you download the latest firmware.  You can grab and install it by running these commands (these will also back up your current firmware to your home folder, so you can revert to it in case the new one proves to be even worse):
```

cp /lib/firmware/iwlwifi-4965-2.ucode ~/home
cd /tmp
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-4965-ucode-228.61.2.24.tgz
tar -xf iwlwifi-4965-ucode-228.61.2.24.tgz
sudo cp iwlwifi-4965-ucode-228.61.2.24 /lib/firmware/iwlwifi-4965-2.ucode 
```

After this, run the following commands to unload and reload the driver, so that the new firmware will take effect:
```

sudo rmmod iwlagn
sudo modprobe iwlagn
```

If your performance issues persist under the new firmware, please now post the output again of:

dmesg | grep -e iwl -e wlan -ie firmware -ie micro

In case there's a problem and the new firmware doesn't allow you to get online at all, you can revert to the old copy by typing:
```

sudo cp ~/iwlwifi-4965-2.ucode /lib/firmware
```

and then unloading/reloading the driver again with:
```

sudo rmmod iwlagn
sudo modprobe iwlagn
```

Let me know if the updated firmware helps.  If not, we can try some other solutions.

---

### Post by Hende86 on 2010-10-21
Hello!
The problem seems to be solved now. My wireless works really good! Thnx alot Pytheas for the help.

---

### Post by Hende86 on 2010-10-21
The firmware update did the trick!

---

### Post by pytheas22 on 2010-10-21
Great to hear that worked.  You can get rid of the iwlwifi-xxx file in your Home folder now if you want; you shouldn't need it anymore.  Hope you enjoy Ubuntu :)

---

### Post by MSwal2846 on 2010-10-27
Hi pytheas22, oh guru of the wireless! :)

I am also having major wireless issues.  Since 10.04 came out, my wireless would work fine for several hours, then, even though NetworkManager said I was connected, I was not.  And coming out of suspend was impossible to get reconnected.

Then I discovered the backport modules.  I installed "linux-backports-modules-wireless-2.6.32-24-generic" and wireless worked amazingly well for several months.  That is up to about 3 weeks ago when an update came in for the backport-modules.  I watched it install thinking to myself "uh-oh" ... and I was right.  Ever since, my wireless is crap.  I've even tried to "go back" but without success.  And it doesn't matter which wireless access point (home, work, coffee shop, customer location, etc) ... so I don't think it's a router issue but my machine.  By the way, I'm using a Lenovo X200 thinkpad.

So, I am writing to solicit your help!!  I am currently using my AT&T wireless WAN card as the wireless is useless ... again.

lspci -nn

> 00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:03.0 Communication controller [0780]: Intel Corporation Mobile 4 Series Chipset MEI Controller [8086:2a44] (rev 07)
00:03.2 IDE interface [0101]: Intel Corporation Mobile 4 Series Chipset PT IDER Controller [8086:2a46] (rev 07)
00:03.3 Serial controller [0700]: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection [8086:2a47] (rev 07)
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]

mswallow-> lsusb
> Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 17ef:480c Lenovo 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 0bdb:1900 Ericsson Business Mobile Networks BV 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

mswallow-> sudo lshw -C Network
> [sudo] password for mswallow: 
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:16:13:26:b1
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.8-3 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f2600000-f261ffff memory:f2625000-f2625fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6b:5b:ac:3e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f2500000-f2501fff
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 3
       logical name: usb0
       serial: 02:80:37:ec:02:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=32.179.134.237 link=yes multicast=yes

mswallow-> uname -rm
2.6.32-25-generic i686

mswallow-> iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"EmergysWirelessNetwork"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

usb0      no wireless extensions.

tun0      no wireless extensions.


Any help would be greatly appreciated!!!

---

### Post by pytheas22 on 2010-10-28
**Mark**: you have two options.  One would be to figure out which version of the backports-modules package was the one that worked, then revert to it.  If it was really only the upgrade of that package that broke things (and not a change somewhere else, like a kernel upgrade), then that should solve it.

You should be able to find out which changes have been made to your backports-modules by typing:
```

grep -i backports-modules /var/log/apt/history.log
```

(Note that it's "backports" and not "backport"--it needs to spelled correctly or the system won't find it :))

If you could post the output of that command, I can hopefully tell you how to get the good version back.  You could then mark the backport-modules package to be "held" at that version, so that you could upgrade the rest of the system without changing the backports-modules package.

The second approach would be to recompile your wireless driver from source using the code from [http://linuxwireless.org](http://linuxwireless.org).  If it's a problem with the driver itself, this should take care of it.  But unless you disagree, let's try the backports-modules approach first, since it would be a bit "cleaner," and certainly simpler than compiling from source.

---

### Post by MSwal2846 on 2010-10-29
Thank you for your quick reply!

I thought that it would be a good idea to go back also.  So I went back through and found, what I thought was the version I had been on and installed that.  You'll see that in the output below.

Unfortunately, either I didn't select the correct package or, as you said, there is something else going on.

Anyway, I will post the output, perhaps you'll see if I screwed this up.  If not, then I'm game to try the compile route ... missing wireless is a not good...

Here is the output:

```
mswallow-> grep -i backports-modules /var/log/apt/history.log
Upgrade: libkrb5-3 (1.8.1+dfsg-2ubuntu0.2, 1.8.1+dfsg-2ubuntu0.3), libkrb5support0 (1.8.1+dfsg-2ubuntu0.2, 1.8.1+dfsg-2ubuntu0.3), screen (4.0.3-14ubuntu1, 4.0.3-14ubuntu1.2), libcouchdb-glib-1.0-2 (0.6.3-0ubuntu1, 0.6.3-0ubuntu2), libk5crypto3 (1.8.1+dfsg-2ubuntu0.2, 1.8.1+dfsg-2ubuntu0.3), coreutils (7.4-2ubuntu2, 7.4-2ubuntu3), python-imaging (1.1.7-1, 1.1.7-1ubuntu0.1), tar (1.22-2, 1.22-2ubuntu1), linux-backports-modules-compat-wireless-2.6.34-2.6.32-25-generic (2.6.32-25.23, 2.6.32-25.24), libdesktopcouch-glib-1.0-2 (0.6.3-0ubuntu1, 0.6.3-0ubuntu2), libssl0.9.8 (0.9.8k-7ubuntu8.1, 0.9.8k-7ubuntu8.2), openssl (0.9.8k-7ubuntu8.1, 0.9.8k-7ubuntu8.2), libgssapi-krb5-2 (1.8.1+dfsg-2ubuntu0.2, 1.8.1+dfsg-2ubuntu0.3)
Install: linux-backports-modules-wireless-2.6.35-lucid-generic (2.6.32.25.27), linux-backports-modules-compat-wireless-2.6.35-2.6.32-25-generic (2.6.32-25.24)
Remove: linux-backports-modules-wireless-lucid-generic (2.6.32.25.27), linux-backports-modules-compat-wireless-2.6.34-2.6.32-25-generic (2.6.32-25.24)
Remove: linux-backports-modules-wireless-2.6.32-24-generic (2.6.32-24.17)
Install: linux-backports-modules-compat-wireless-2.6.34-2.6.32-25-generic (2.6.32-25.24)
Remove: linux-backports-modules-wireless-2.6.35-lucid-generic (2.6.32.25.27), linux-backports-modules-compat-wireless-2.6.35-2.6.32-25-generic (2.6.32-25.24)
Remove: linux-backports-modules-compat-wireless-2.6.34-2.6.32-25-generic (2.6.32-25.24)
Install: linux-backports-modules-wireless-2.6.32-24-generic (2.6.32-24.17)
```

By the way, sorry for not putting the other info in a "code" box...

---

### Post by blue123 on 2010-10-29
hey pytheas22, id also like to get your advice :)

here's the output:

lspci -nn

```
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) [1022:9607]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]
01:05.1 Audio device [0403]: ATI Technologies Inc RS780 Azalia controller [1002:960f]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)

```


lsusb

```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b1b4 Chicony Electronics Co., Ltd Lenovo Integrated Camera
Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lshhw -C Network
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 60:eb:69:02:6f:a0
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:42 ioport:a000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff memory:d0020000-d003ffff
  *-network
       description: Wireless interface
       product: RTL8191SEvB Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: 70:f1:a1:df:33:1a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0017.0507.2010 firmware=63 ip=192.168.0.36 latency=0 link=yes multicast=yes wireless=802.11bg
       resources: irq:19 ioport:b000(size=256) memory:d0300000-d0303fff

```

uname -rm

```
2.6.35-22-generic i686
```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  ESSID:"asdf"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0F:CB:FF:56:2A   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=100/100  Signal level=-45 dBm  Noise level=-120 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


My wlan works absolutely fine at home but i get disconnected like every 30s at uni. Hope you can help, thanks!

---

### Post by pytheas22 on 2010-10-29
**MSwal2846**: it looks like you did revert to the earlier version of the backports-modules package.  Sorry to hear it didn't make a difference.  (I assume you rebooted after reverting the package; otherwise the changes would not have taken effect.  In case you didn't, give that a try!)

To compile from source, first go to [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6) and download the file named "compat-wireless-2.6.tar.bz2" (if you don't see a list of files the first time you load that link, try reloading it; that site does some obnoxious things with anti-hotlinking that can cause problems if you've never visited it before).  Save the file to your desktop, then run:

```
sudo apt-get update
sudo apt-get install build-essential
cd ~/Desktop
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make
sudo make unload
sudo make load
sudo make install
```

Now reboot and hopefully your wireless will be better.  If not, let me know, and please let me know also the output of:
```

dmesg | grep -e wlan -e iwl
lshw -C Network
modinfo iwlagn
```
[B]
blue123[/B]: thanks for the information.  It would be good to see also the output of:

```
dmesg | grep -e wlan -e rtl
```

Does your university network use encryption?  If so, do you know which kind (WPA1, WPA2, WPA1 and WPA2, WPA enterprise)?  Are you using encryption on your home network as well, and if so what do you use there?

I ask because my first guess would be that your troubles are encryption-related.  That can sometimes be the result of a driver issue and you would need to update the driver or choose a different driver (such as ndiswrapper), but in other cases, simply using a different connection manager could also work.  If you haven't tried [wicd]("http://wicd.sourceforge.net"), I would see if it performs any better than NetworkManager.  You can install wicd by typing:
```

sudo apt-get install wicd
```

Then stop NetworkManager with:
```

sudo /etc/init.d/network-manager stop
```

and then launch wicd from the Applications>Internet menu and see if it keeps you connected at the university.  Note that with wicd, you have to enter the WPA passphrase before attempting to connect--it does not automatically prompt you like NetworkManager does.

---

### Post by blue123 on 2010-10-30
> **pytheas22 said:**
> [B]
blue123[/B]: thanks for the information.  It would be good to see also the output of:

```
dmesg | grep -e wlan -e rtl
```Does your university network use encryption?  If so, do you know which kind (WPA1, WPA2, WPA1 and WPA2, WPA enterprise)?  Are you using encryption on your home network as well, and if so what do you use there?

I ask because my first guess would be that your troubles are encryption-related.  That can sometimes be the result of a driver issue and you would need to update the driver or choose a different driver (such as ndiswrapper), but in other cases, simply using a different connection manager could also work.  If you haven't tried [wicd]("http://wicd.sourceforge.net"), I would see if it performs any better than NetworkManager.  You can install wicd by typing:
```

sudo apt-get install wicd
```Then stop NetworkManager with:
```

sudo /etc/init.d/network-manager stop
```and then launch wicd from the Applications>Internet menu and see if it keeps you connected at the university.  Note that with wicd, you have to enter the WPA passphrase before attempting to connect--it does not automatically prompt you like NetworkManager does.

Thanks for your answer! Ill post the wlan log as soon as i get back to uni. The current one probably wont help you? I remember getting some weird OpenSSL error msgs tho. I use WEP (^^) at home and WPA2 Enterprise TLS EAP at uni. Ive already tried using another network manager but got the same disconnects. If it's an encryption issue, will another driver such as ndiswrapper solve it?

---

### Post by pytheas22 on 2010-10-30
> Thanks for your answer! Ill post the wlan log as soon as i get back to uni. The current one probably wont help you? I remember getting some weird OpenSSL error msgs tho. I use WEP (^^) at home and WPA2 Enterprise TLS EAP at uni. Ive already tried using another network manager but got the same disconnects. If it's an encryption issue, will another driver such as ndiswrapper solve it?

Yes, I would need to see the dmesg output after a disconnect to see what the system thinks went wrong.  And if it is an encryption issue, it's hard to say for sure whether a different driver, such as ndiswrapper, would solve it, unless we're able to pinpoint exactly where the problem is occuring, it's hard to know for sure, but it's likely.  I'll look forward to your logs when you're able to post them.

---

### Post by facebuntu on 2010-10-31
Hi pytheas22,

I have a Broadcom BCM43224 wireless and am on x64 bit.  I've got issue with the Broadcom STA drivers where it gives me high latency to any wireless APs.  From 1ms to 300ms so throughput suffers as a result.  This happened post 10.10 upgrade (not fresh install) from 10.04 (had no issues on 10.04)

Do you know if I can use ndiswrapper with a windows x64 drivers for this chip?  I'm still new to ubuntu so any help would be much appreciated.

I've tried removing all wireless driver then reinstalling the BC STA drivers.

```
lspci -nn | grep Network
44:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)

uname -rm
2.6.35-22-generic x86_64

sudo lshw -C Network 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:44:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d0600000-d0603fff

```

I don't have any wireless drivers installed at the moment.

---

### Post by mpolzin2011 on 2010-10-31
pytheas22 could you help me too? i am have sooo much trouble getting wireless working.

not sure what codes you would like me to use to help you gather information, but if you give me some, ill be happy to provide you the info

EDIT: i am also using ubuntu 10.10


EDIT: i was reading thorugh your guide on how to troubleshoot ndiswrapper and it said it wasnt installed. then proceeded to tell me to install it enter

sudo apt-get install ndiswrapper-common

when i entered that, it replied saying 

E: could not get the loc /var/lib/dpkg/lock - open (11: resource temporarily unavailable)
E: unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by omarly on 2010-10-31
#55 did it for me :)
after getting the wireless up at EVERY boot, i was so satisfied, but resently got some problems with stability.
seached the forum on wireless and intel - had a shot at the wireless-site, visited a lot of times earlier to get the wifi up and going, and now it seems like better than ever.

thx again

you guys r awsome :)

---

### Post by pytheas22 on 2010-11-01
**facebuntu**: you should be able to use ndiswrapper to drive your card, assuming you can find the right Windows drivers.  From the output you posted, it looks like you've successfully deactivated the STA driver, so now it should be a matter just of installing the ndiswrapper-common and ndiswrapper-utils-1.9 packages, if you haven't already, then loading the Windows driver into them.  There are lots of instructions available around the Internet for using ndiswrapper so I won't duplicate them here, but let me know if you need help figuring that out.

Once ndiswrapper is installed and the Windows drivers are loaded into it, reboot and hopefully your connection will be less flaky.
[B]
mpolzin2011[/B]: the error message you received while trying to install ndiswrapper usually means that another process is trying to install packages at the same time.  If you had Ubuntu Software Center open, try closing it, then running the commands again.

What issues are you suffering more generally?  Does your wireless card not work at all, or does it just not work well?  Which hardware do you have?  If you don't know, please post the output of:
```

lspci -nn
lsusb
lshw -C Network
uname -a
```

**omarly**: glad to hear it worked for you :)  Keep in mind that whenever you update your kernel via Ubuntu Updates, you may need to recompile the driver (unless the wireless works fine in the updated kernel, in which you can leave it be).

---

### Post by mpolzin2011 on 2010-11-01
lspci -nm

00:00.0 "0600" "8086" "2a40" -r07 "103c" "3603"
00:01.0 "0604" "8086" "2a41" -r07 "" ""
00:1a.0 "0c03" "8086" "2937" -r03 "103c" "3603"
00:1a.1 "0c03" "8086" "2938" -r03 "103c" "3603"
00:1a.7 "0c03" "8086" "293c" -r03 -p20 "103c" "3603"
00:1b.0 "0403" "8086" "293e" -r03 "103c" "3603"
00:1c.0 "0604" "8086" "2940" -r03 "" ""
00:1c.1 "0604" "8086" "2942" -r03 "" ""
00:1c.2 "0604" "8086" "2944" -r03 "" ""
00:1c.3 "0604" "8086" "2946" -r03 "" ""
00:1c.4 "0604" "8086" "2948" -r03 "" ""
00:1c.5 "0604" "8086" "294a" -r03 "" ""
00:1d.0 "0c03" "8086" "2934" -r03 "103c" "3603"
00:1d.1 "0c03" "8086" "2935" -r03 "103c" "3603"
00:1d.2 "0c03" "8086" "2936" -r03 "103c" "3603"
00:1d.3 "0c03" "8086" "2939" -r03 "103c" "3603"
00:1d.7 "0c03" "8086" "293a" -r03 -p20 "103c" "3603"
00:1e.0 "0604" "8086" "2448" -r93 -p01 "" ""
00:1f.0 "0601" "8086" "2919" -r03 "103c" "3603"
00:1f.2 "0106" "8086" "2929" -r03 -p01 "103c" "3603"
00:1f.3 "0c05" "8086" "2930" -r03 "103c" "3603"
00:1f.6 "1180" "8086" "2932" -r03 "103c" "3603"
01:00.0 "0300" "10de" "06e8" -ra1 "103c" "3603"
02:00.0 "0280" "14e4" "4315" -r01 "103c" "137c"
03:00.0 "0200" "10ec" "8168" -r02 "103c" "3603"
06:00.0 "0c00" "197b" "2380" -p10 "103c" "3603"
06:00.1 "0880" "197b" "2382" "103c" "3603"
06:00.2 "0805" "197b" "2381" -p01 "103c" "3603"
06:00.3 "0880" "197b" "2383" "103c" "3603"
06:00.4 "0880" "197b" "2384" "103c" "3603"


lsusb

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 064e:c107 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lshw -c network

WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:9e200000-9e203fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:ec:af:8c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.104 latency=0 multicast=yes
       resources: irq:32 ioport:6000(size=256) memory:94010000-94010fff(prefetchable) memory:94000000-9400ffff(prefetchable) memory:94020000-9402ffff(prefetchable)




uname -a

Linux ubuntu 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux


EDIT:  when i typed in sudo apt-get install nidswrapper-common

and it starts to look like its gonna install, 
but then it says this.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ndiswrapper-source
The following NEW packages will be installed:
  ndiswrapper-common
0 upgraded, 1 newly installed, 0 to remove and 131 not upgraded.
Need to get 0B/21.7kB of archives.
After this operation, 98.3kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)'
in the drive '/cdrom/' and press enter


i dont have a cd? i downloaded this off the internet.



thanks

Matt

---

### Post by pytheas22 on 2010-11-01
**mpolzin2011**: open a terminal and type:

```
sudo software-properties-gtk
```

A window will open.  Under the "Ubuntu Software" tab, uncheck the box for using the Ubuntu CD as a repository.  Then close the window, agree to reload the sources list when prompted, and then try reinstalling ndiswrapper.  It should work, and you should then be able to get your card running using the Windows drivers (once you load them into ndiswrapper).

---

### Post by pytheas22 on 2010-11-02
newboyo, mpolzin2011, se7ensense7en: I moved your posts to new threads and replied in those, because this thread is getting a little crazy.  I'm happy to keep helping you but it will be easier to keep track of everything in a separate thread for each issue.

The threads are: [http://ubuntuforums.org/showthread.php?t=1612091](http://ubuntuforums.org/showthread.php?t=1612091) [http://ubuntuforums.org/showthread.php?t=1612095](http://ubuntuforums.org/showthread.php?t=1612095) [http://ubuntuforums.org/showthread.php?t=1612096](http://ubuntuforums.org/showthread.php?t=1612096)

---

### Post by MSwal2846 on 2010-11-03
Thank you, pytheas22.  I have downloaded, compiled and loaded the module(s).  So now we'll see.  I'll report back in a few days.

Thank you for your help!

---

### Post by MSwal2846 on 2010-11-05
I want to report back, pytheas22, that the improvement in my wireless connection is night and day!  I am almost instantaneously reconnected upon resuming from suspending, which previously would take several seconds, if it occurred at all.

I understand that I will need to watch for kernel changes and potential recompile based on that, but I'll gladly "pay that price."  

Thank you, again, for your help!

---

### Post by pytheas22 on 2010-11-05
Mark: thanks for reporting back and great to here it worked :)  Hopefully the issue itself will be fixed soon (I'm not positive, but [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/525902?comments=all") looks like it might be relevant; unfortunately it has not yet been addressed at the moment).

---

### Post by MSwal2846 on 2010-11-26
I just wanted to keep this up to date to save anyone else having issues with wireless connectivity.

The issue of not being able to reconnect wirelessly continues with Ubuntu 10.10 maverick.

Following the directions described previously for me in this thread worked great!

---

