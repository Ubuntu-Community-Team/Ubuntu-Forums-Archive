---
title: "xubuntu slow wireless"
date: 2011-06-02
forum: Networking &amp; Wireless
---

### Post by jpin321 on 2011-06-02
I've read other posts simular to this but I can't seem to find any solution that helps.

I have a new install of xubuntu 11.04.  I have the same issue on ubuntu 10.04.

I'm using a wireless lynksys card don't know the exact model at this time I'm not at the PC.  The problem is wirless is simply sloowwww.  Funny thing is I can connect my phone to my wifi and usb teather it to my xubuntu box and it absolutely screems along.

What gives I don't get it?  It acts like it doesn't like the driver or something?  I've also tried a belkin card with the same results.   Also if I put two wireless cards in at the same time xubuntu refuses to see either card, wtf linux.

Unfortunately I'm a windows admin (I know ;) )  so when it comes to linux issues I'm not even sure where to start.

Help me forum..

---

### Post by Toz on 2011-06-03
Here is a link to an ubuntu wireless information page: [https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs) and a troubleshooting guide: [https://help.ubuntu.com/community/WirelessTroubleshootingProcedure](https://help.ubuntu.com/community/WirelessTroubleshootingProcedure)

Since you didn't provide any relevant information to assist with troubleshooting, can you open a terminal window, type in the following commands, and post back with the replies:```
sudo lshw -C network
rfkill list
sudo iwlist scanning
cat /etc/network/interfaces
cat /etc/lsb-release
lspci -nn
lsusb
uname -a
dmesg | egrep '8180|acx|at76|ath|b43|bcm|brcm|CX|eth|ipw|ireless|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|rt5|rt6|rt7|usb|witch|wl'
sudo dmidecode|egrep 'Manufact|Product'
iwconfig
sudo lsmod
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by jpin321 on 2011-06-03
SCSI                      

  *-network:0      
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:15:f2:4a:11:7d
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:21 ioport:d400(size=256) memory:fddff000-fddff0ff
  *-network:1
       description: Wireless interface
       product: RT2500 802.11g
       vendor: Ralink corp.
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: wlan0
       version: 01
       serial: 00:12:17:8a:72:1e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.109 latency=64 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:fddfc000-fddfdfff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: da:fe:d8:93:e8:38
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=172.20.23.253 link=yes multicast=yes

---

### Post by Toz on 2011-06-03
Can you please run each one of those commands individually and post back the results for each command?

---

### Post by Toz on 2011-06-03
Based on the info you did send, you have the RT2500 chip. There is a whole thread devoted to making this card work. Have a look at: [http://ubuntuforums.org/showthread.php?t=1211513&highlight=RT2500](http://ubuntuforums.org/showthread.php?t=1211513&highlight=RT2500) (specifically post #11 & post #37)

---

### Post by jpin321 on 2011-06-04
#toc, .toc, .mw-warning { border: 1px solid rgb(170, 170, 170); background-color: rgb(249, 249, 249); padding: 5px; font-size: 95%; }#toc h2, .toc h2 { display: inline; border: medium none; padding: 0pt; font-size: 100%; font-weight: bold; }#toc #toctitle, .toc #toctitle, #toc .toctitle, .toc .toctitle { text-align: center; }#toc ul, .toc ul { list-style-type: none; list-style-image: none; margin-left: 0pt; padding-left: 0pt; text-align: left; }#toc ul ul, .toc ul ul { margin: 0pt 0pt 0pt 2em; }#toc .toctoggle, .toc .toctoggle { font-size: 94%; }body { font-family: 'Times New Roman'; color: rgb(0, 0, 0); widows: 2; font-style: normal; text-indent: 0in; font-variant: normal; font-weight: normal; font-size: 12pt; text-decoration: none; text-align: left; }table {  }td { border-collapse: collapse; text-align: left; vertical-align: top; }p, h1, h2, h3, li { color: rgb(0, 0, 0); font-family: 'Times New Roman'; font-size: 12pt; text-align: left; }         [LEFT]brandon@brandon-xubuntu:~$ sudo lshw -C network[/LEFT]
    [LEFT][sudo] password for brandon: [/LEFT]
    [LEFT]Sorry, try again.[/LEFT]
    [LEFT][sudo] password for brandon: [/LEFT]
    [LEFT]  *-network:0             [/LEFT]
    [LEFT]       description: Ethernet interface[/LEFT]
    [LEFT]       product: RTL-8139/8139C/8139C+[/LEFT]
    [LEFT]       vendor: Realtek Semiconductor Co., Ltd.[/LEFT]
    [LEFT]       physical id: 3[/LEFT]
    [LEFT]       bus info: pci@0000:02:03.0[/LEFT]
    [LEFT]       logical name: eth0[/LEFT]
    [LEFT]       version: 10[/LEFT]
    [LEFT]       serial: 00:15:f2:4a:11:7d[/LEFT]
    [LEFT]       size: 10Mbit/s[/LEFT]
    [LEFT]       capacity: 100Mbit/s[/LEFT]
    [LEFT]       width: 32 bits[/LEFT]
    [LEFT]       clock: 33MHz[/LEFT]
    [LEFT]       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/LEFT]
    [LEFT]       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s[/LEFT]
    [LEFT]       resources: irq:21 ioport:d400(size=256) memory:fddff000-fddff0ff[/LEFT]
    [LEFT]  *-network:1[/LEFT]
    [LEFT]       description: Wireless interface[/LEFT]
    [LEFT]       product: RT2500 802.11g[/LEFT]
    [LEFT]       vendor: Ralink corp.[/LEFT]
    [LEFT]       physical id: 8[/LEFT]
    [LEFT]       bus info: pci@0000:02:08.0[/LEFT]
    [LEFT]       logical name: wlan0[/LEFT]
    [LEFT]       version: 01[/LEFT]
    [LEFT]       serial: 00:12:17:8a:72:1e[/LEFT]
    [LEFT]       width: 32 bits[/LEFT]
    [LEFT]       clock: 33MHz[/LEFT]
    [LEFT]       capabilities: pm bus_master cap_list ethernet physical wireless[/LEFT]
    [LEFT]       configuration: broadcast=yes driver=rt2500pci driverversion=2.6.38-8-generic firmware=N/A ip=192.168.1.109 latency=64 link=yes multicast=yes wireless=IEEE 802.11bg[/LEFT]
    [LEFT]       resources: irq:16 memory:fddfc000-fddfdfff[/LEFT]
    [LEFT]brandon@brandon-xubuntu:~$ rfkill list[/LEFT]
    [LEFT]0: phy0: Wireless LAN[/LEFT]
    [LEFT]	Soft blocked: no[/LEFT]
    [LEFT]	Hard blocked: no[/LEFT]
    [LEFT]brandon@brandon-xubuntu:~$ sudo iwlist scanning[/LEFT]
    [LEFT]lo        Interface doesn't support scanning.[/LEFT]
    [LEFT][/LEFT]
    [LEFT]eth0      Interface doesn't support scanning.[/LEFT]
    [LEFT][/LEFT]
    [LEFT]wlan0     Interface doesn't support scanning : Device or resource busy[/LEFT]
    [LEFT][/LEFT]
    [LEFT]brandon@brandon-xubuntu:~$ cat /etc/network/interfaces[/LEFT]
    [LEFT]auto lo[/LEFT]
    [LEFT]iface lo inet loopback[/LEFT]
    [LEFT][/LEFT]
    [LEFT]brandon@brandon-xubuntu:~$ cat /etc/lsb-release[/LEFT]
    [LEFT]DISTRIB_ID=Ubuntu[/LEFT]
    [LEFT]DISTRIB_RELEASE=11.04[/LEFT]
    [LEFT]DISTRIB_CODENAME=natty[/LEFT]
    [LEFT]DISTRIB_DESCRIPTION="Ubuntu 11.04"[/LEFT]
    [LEFT]brandon@brandon-xubuntu:~$ lspci -nn[/LEFT]
    [LEFT]00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)[/LEFT]
    [LEFT]00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f][/LEFT]
    [LEFT]00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374][/LEFT]
    [LEFT]00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375][/LEFT]
    [LEFT]00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373][/LEFT]
    [LEFT]00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)[/LEFT]
    [LEFT]00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376][/LEFT]
    [LEFT]00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377][/LEFT]
    [LEFT]00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371][/LEFT]
    [LEFT]00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)[/LEFT]
    [LEFT]00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100][/LEFT]
    [LEFT]00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101][/LEFT]
    [LEFT]00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102][/LEFT]
    [LEFT]00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103][/LEFT]
    [LEFT]01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS480 [Radeon Xpress 200G Series] [1002:5954][/LEFT]
    [LEFT]02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)[/LEFT]
    [LEFT]02:05.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 80)[/LEFT]
    [LEFT]02:08.0 Network controller [0280]: Ralink corp. RT2500 802.11g [1814:0201] (rev 01)[/LEFT]
    [LEFT]02:09.0 RAID bus controller [0104]: VIA Technologies, Inc. VT6421 IDE RAID Controller [1106:3249] (rev 50)[/LEFT]
    [LEFT]02:0a.0 Communication controller [0780]: Conexant Systems, Inc. HSF 56k Data/Fax Modem [14f1:2f20][/LEFT]
    [LEFT]brandon@brandon-xubuntu:~$ lsusb[/LEFT]
    [LEFT]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/LEFT]
    [LEFT]Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader[/LEFT]
    [LEFT]Bus 002 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever[/LEFT]
    [LEFT]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/LEFT]
    [LEFT]Bus 001 Device 002: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 flash drive[/LEFT]
    [LEFT]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/LEFT]
    [LEFT]brandon@brandon-xubuntu:~$ uname -a[/LEFT]
    [LEFT]Linux brandon-xubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux[/LEFT]
    [LEFT]brandon@brandon-xubuntu:~$ dmesg | egrep '8180|acx|at76|ath|b43|bcm|brcm|CX|eth|ipw|ireless|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|ound|p54|prism|rtl|rt2|rt3|rt5|rt6|rt7|usb|witch|wl'[/LEFT]
    [LEFT][    0.000000] No AGP bridge found[/LEFT]
    [LEFT][    0.000000] found SMP MP-table at [ffff8800000f6010] f6010[/LEFT]
    [LEFT][    0.000000] ACPI: SRAT 000000004bef8180 00090 (v01 HP-CPC HAMMER   00000001 AMD  00000001)[/LEFT]
    [LEFT][    0.000000] No AGP bridge found[/LEFT]
    [LEFT][    0.025943] SMP alternatives: switching to UP code[/LEFT]
    [LEFT][    0.177398] ACPI: No dock devices found.[/LEFT]
    [LEFT][    0.177401] HEST: Table not found.[/LEFT]
    [LEFT][    0.187885] usbcore: registered new interface driver usbfs[/LEFT]
    [LEFT][    0.187897] usbcore: registered new interface driver hub[/LEFT]
    [LEFT][    0.187932] usbcore: registered new device driver usb[/LEFT]
    [LEFT][    0.201413] pnp: PnP ACPI: found 11 devices[/LEFT]
    [LEFT][    0.207815] Switching to clocksource acpi_pm[/LEFT]
    [LEFT][    0.209651] Switched to NOHz mode on CPU #0[/LEFT]
    [LEFT][    0.364357] ERST: Table is not found![/LEFT]
    [LEFT][    0.367810] i2c-core: driver [adp5520] using legacy suspend method[/LEFT]
    [LEFT][    0.367811] i2c-core: driver [adp5520] using legacy resume method[/LEFT]
    [LEFT][    0.400469] hub 1-0:1.0: USB hub found[/LEFT]
    [LEFT][    0.474461] hub 2-0:1.0: USB hub found[/LEFT]
    [LEFT][    0.544511] hub 3-0:1.0: USB hub found[/LEFT]
    [LEFT][    0.549011] device-mapper: multipath: version 1.2.0 loaded[/LEFT]
    [LEFT][    0.549019] device-mapper: multipath round-robin: version 1.0.0 loaded[/LEFT]
    [LEFT][    0.555975] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3800+ (1 cpu cores) (version 2.20.00)[/LEFT]
    [LEFT][    0.556610] usbmon usbmon3: hash matches[/LEFT]
    [LEFT][    0.556781] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found[/LEFT]
    [LEFT][    0.720089] usb 1-2: new high speed USB device using ehci_hcd and address 2[/LEFT]
    [LEFT][    0.971297] usbcore: registered new interface driver uas[/LEFT]
    [LEFT][    1.390035] usb 2-2: new low speed USB device using ohci_hcd and address 2[/LEFT]
    [LEFT][    1.906501] scsi5 : usb-storage 1-2:1.0[/LEFT]
    [LEFT][    1.908786] usbcore: registered new interface driver usb-storage[/LEFT]
    [LEFT][    1.918315] input: Microsoft Microsoft Wireless Optical Mouse® 1.00 as /devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.0/input/input3[/LEFT]
    [LEFT][    1.918554] generic-usb 0003:045E:00E1.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse® 1.00] on usb-0000:00:13.0-2/input0[/LEFT]
    [LEFT][    1.918839] usbcore: registered new interface driver usbhid[/LEFT]
    [LEFT][    1.918842] usbhid: USB HID core driver[/LEFT]
    [LEFT][    1.950135] usb 2-4: new full speed USB device using ohci_hcd and address 3[/LEFT]
    [LEFT][    1.983149] 8139too 0000:02:03.0: eth0: RealTek RTL8139 at 0xd400, 00:15:f2:4a:11:7d, IRQ 21[/LEFT]
    [LEFT][    2.180552] scsi6 : usb-storage 2-4:1.0[/LEFT]
    [LEFT][    7.589274] lp: driver loaded but no devices found[/LEFT]
    [LEFT][    9.248197] rt2500pci 0000:02:08.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16[/LEFT]
    [LEFT][    9.624251] Registered led device: rt2500pci-phy0::radio[/LEFT]
    [LEFT][    9.624272] Registered led device: rt2500pci-phy0::quality[/LEFT]
    [LEFT][   10.301223] Console: switching to colour frame buffer device 180x56[/LEFT]
    [LEFT][   18.587510] eth0: link down[/LEFT]
    [LEFT][   18.588156] ADDRCONF(NETDEV_UP): eth0: link is not ready[/LEFT]
    [LEFT][   19.051104] ADDRCONF(NETDEV_UP): wlan0: link is not ready[/LEFT]
    [LEFT][65723.300046] usb 1-6: new high speed USB device using ehci_hcd and address 5[/LEFT]
    [LEFT][65723.462819] scsi7 : usb-storage 1-6:1.0[/LEFT]
    [LEFT][65733.708913] usb 1-6: USB disconnect, address 5[/LEFT]
    [LEFT][65734.110037] usb 1-6: new high speed USB device using ehci_hcd and address 6[/LEFT]
    [LEFT][65734.344802] usbcore: registered new interface driver cdc_ether[/LEFT]
    [LEFT][65734.363197] rndis_host 1-6:1.0: usb0: register 'rndis_host' at usb-0000:00:13.2-6, RNDIS device, da:fe:d8:93:e8:38[/LEFT]
    [LEFT][65734.365293] usbcore: registered new interface driver rndis_host[/LEFT]
    [LEFT][65744.540171] usb0: no IPv6 routers present[/LEFT]
    [LEFT][65753.252065] wlan0: authenticate with 00:1b:2f:63:ad:be (try 1)[/LEFT]
    [LEFT][65753.450116] wlan0: authenticate with 00:1b:2f:63:ad:be (try 2)[/LEFT]
    [LEFT][65753.650134] wlan0: authenticate with 00:1b:2f:63:ad:be (try 3)[/LEFT]
    [LEFT][65753.850111] wlan0: authentication with 00:1b:2f:63:ad:be timed out[/LEFT]
    [LEFT][65764.612227] wlan0: authenticate with 00:1b:2f:63:ad:be (try 1)[/LEFT]
    [LEFT][65764.613875] wlan0: authenticated[/LEFT]
    [LEFT][65764.613938] wlan0: associate with 00:1b:2f:63:ad:be (try 1)[/LEFT]
    [LEFT][65764.625107] wlan0: RX AssocResp from 00:1b:2f:63:ad:be (capab=0x431 status=0 aid=4)[/LEFT]
    [LEFT][65764.625116] wlan0: associated[/LEFT]
    [LEFT][65764.626581] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready[/LEFT]
    [LEFT][65775.390030] wlan0: no IPv6 routers present[/LEFT]
    [LEFT][66526.765555] usb 1-6: USB disconnect, address 6[/LEFT]
    [LEFT][66526.765747] rndis_host 1-6:1.0: usb0: unregister 'rndis_host' usb-0000:00:13.2-6, RNDIS device[/LEFT]
    [LEFT][66527.150068] usb 1-6: new high speed USB device using ehci_hcd and address 7[/LEFT]
    [LEFT][66527.318841] scsi8 : usb-storage 1-6:1.0[/LEFT]
    [LEFT][66530.412413] usb 1-6: USB disconnect, address 7[/LEFT]
    [LEFT][68965.710037] ieee80211 phy0: wlan0: No probe response from AP 00:1b:2f:63:ad:be after 500ms, disconnecting.[/LEFT]
    [LEFT][68967.163716] wlan0: authenticate with 00:1b:2f:63:ad:be (try 1)[/LEFT]
    [LEFT][68967.360067] wlan0: authenticate with 00:1b:2f:63:ad:be (try 2)[/LEFT]
    [LEFT][68967.560038] wlan0: authenticate with 00:1b:2f:63:ad:be (try 3)[/LEFT]
    [LEFT][68967.760036] wlan0: authentication with 00:1b:2f:63:ad:be timed out[/LEFT]
    [LEFT][69016.502141] wlan0: authenticate with 00:1b:2f:63:ad:be (try 1)[/LEFT]
    [LEFT][69016.700046] wlan0: authenticate with 00:1b:2f:63:ad:be (try 2)[/LEFT]
    [LEFT][69016.900045] wlan0: authenticate with 00:1b:2f:63:ad:be (try 3)[/LEFT]
    [LEFT][69016.904595] wlan0: authenticated[/LEFT]
    [LEFT][69018.900830] wlan0: associate with 00:1b:2f:63:ad:be (try 1)[/LEFT]
    [LEFT][69019.100047] wlan0: associate with 00:1b:2f:63:ad:be (try 2)[/LEFT]
    [LEFT][69019.300047] wlan0: associate with 00:1b:2f:63:ad:be (try 3)[/LEFT]
    [LEFT][69019.304387] wlan0: RX AssocResp from 00:1b:2f:63:ad:be (capab=0x431 status=0 aid=5)[/LEFT]
    [LEFT][69019.304394] wlan0: associated[/LEFT]
    [LEFT][69029.307241] wlan0: deauthenticating from 00:1b:2f:63:ad:be by local choice (reason=3)[/LEFT]
    [LEFT][69030.672062] wlan0: authenticate with 00:1b:2f:63:ad:be (try 1)[/LEFT]
    [LEFT][69030.870036] wlan0: authenticate with 00:1b:2f:63:ad:be (try 2)[/LEFT]
    [LEFT][69031.070043] wlan0: authenticate with 00:1b:2f:63:ad:be (try 3)[/LEFT]
    [LEFT][69031.270061] wlan0: authentication with 00:1b:2f:63:ad:be timed out[/LEFT]
    [LEFT][89415.903084] wlan0: authenticate with 00:1b:2f:63:ad:be (try 1)[/LEFT]
    [LEFT][89415.904616] wlan0: authenticated[/LEFT]
    [LEFT][89415.904676] wlan0: associate with 00:1b:2f:63:ad:be (try 1)[/LEFT]
    [LEFT][89415.906979] wlan0: RX AssocResp from 00:1b:2f:63:ad:be (capab=0x431 status=0 aid=6)[/LEFT]
    [LEFT][89415.906990] wlan0: associated[/LEFT]
    [LEFT]brandon@brandon-xubuntu:~$ sudo dmidecode|egrep 'Manufact|Product'[/LEFT]
    [LEFT]	Manufacturer: HP Pavilion 061[/LEFT]
    [LEFT]	Product Name: EL466AA-ABA a1330n[/LEFT]
    [LEFT]	Manufacturer: ASUSTek Computer INC.[/LEFT]
    [LEFT]	Product Name: Amberine M[/LEFT]
    [LEFT]	Manufacturer:  [/LEFT]
    [LEFT]	Manufacturer: AMD[/LEFT]
    [LEFT]	Manufacturer: Null[/LEFT]
    [LEFT]	Manufacturer: None[/LEFT]
    [LEFT]	Manufacturer: None[/LEFT]
    [LEFT]	Manufacturer: None[/LEFT]
    [LEFT]	Manufacturer: None[/LEFT]
    [LEFT]brandon@brandon-xubuntu:~$ sudo dmidecode|egrep 'Manufact|Product'[/LEFT]
    [LEFT]	Manufacturer: HP Pavilion 061[/LEFT]
    [LEFT]	Product Name: EL466AA-ABA a1330n[/LEFT]
    [LEFT]	Manufacturer: ASUSTek Computer INC.[/LEFT]
    [LEFT]	Product Name: Amberine M[/LEFT]
    [LEFT]	Manufacturer:  [/LEFT]
    [LEFT]	Manufacturer: AMD[/LEFT]
    [LEFT]	Manufacturer: Null[/LEFT]
    [LEFT]	Manufacturer: None[/LEFT]
    [LEFT]	Manufacturer: None[/LEFT]
    [LEFT]	Manufacturer: None[/LEFT]
    [LEFT]	Manufacturer: None[/LEFT]
    [LEFT]brandon@brandon-xubuntu:~$ iwconfig[/LEFT]
    [LEFT]lo        no wireless extensions.[/LEFT]
    [LEFT][/LEFT]
    [LEFT]eth0      no wireless extensions.[/LEFT]
    [LEFT][/LEFT]
    [LEFT]wlan0     IEEE 802.11bg  ESSID:"netgear"  [/LEFT]
    [LEFT]          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:1B:2F:63:AD:BE   [/LEFT]
    [LEFT]          Bit Rate=48 Mb/s   Tx-Power=20 dBm   [/LEFT]
    [LEFT]          Retry  long limit:7   RTS thr:off   Fragment thr:off[/LEFT]
    [LEFT]          Power Management:off[/LEFT]
    [LEFT]          Link Quality=37/70  Signal level=-73 dBm  [/LEFT]
    [LEFT]          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0[/LEFT]
    [LEFT]          Tx excessive retries:8  Invalid misc:97   Missed beacon:0[/LEFT]
    [LEFT][/LEFT]
    [LEFT]brandon@brandon-xubuntu:~$ sudo lsmod[/LEFT]
    [LEFT]Module                  Size  Used by[/LEFT]
    [LEFT]cryptd                 20510  0 [/LEFT]
    [LEFT]aes_x86_64             17208  1 [/LEFT]
    [LEFT]aes_generic            38279  1 aes_x86_64[/LEFT]
    [LEFT]rndis_host             13801  0 [/LEFT]
    [LEFT]cdc_ether              13208  1 rndis_host[/LEFT]
    [LEFT]usbnet                 26165  2 rndis_host,cdc_ether[/LEFT]
    [LEFT]snd_atiixp             20072  3 [/LEFT]
    [LEFT]snd_ac97_codec        134270  1 snd_atiixp[/LEFT]
    [LEFT]ac97_bus               12730  1 snd_ac97_codec[/LEFT]
    [LEFT]snd_pcm                96625  2 snd_atiixp,snd_ac97_codec[/LEFT]
    [LEFT]snd_seq_midi           13324  0 [/LEFT]
    [LEFT]snd_rawmidi            30486  1 snd_seq_midi[/LEFT]
    [LEFT]snd_seq_midi_event     14899  1 snd_seq_midi[/LEFT]
    [LEFT]snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event[/LEFT]
    [LEFT]snd_timer              29602  2 snd_pcm,snd_seq[/LEFT]
    [LEFT]snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq[/LEFT]
    [LEFT]radeon                982197  2 [/LEFT]
    [LEFT]ttm                    76664  1 radeon[/LEFT]
    [LEFT]drm_kms_helper         42136  1 radeon[/LEFT]
    [LEFT]arc4                   12529  2 [/LEFT]
    [LEFT]rt2500pci              27422  0 [/LEFT]
    [LEFT]rt2x00pci              14322  1 rt2500pci[/LEFT]
    [LEFT]rt2x00lib              49235  2 rt2500pci,rt2x00pci[/LEFT]
    [LEFT]edac_core              53845  0 [/LEFT]
    [LEFT]mac80211              294370  2 rt2x00pci,rt2x00lib[/LEFT]
    [LEFT]drm                   227495  4 radeon,ttm,drm_kms_helper[/LEFT]
    [LEFT]edac_mce_amd           23464  0 [/LEFT]
    [LEFT]i2c_algo_bit           13400  1 radeon[/LEFT]
    [LEFT]snd                    67382  13 snd_atiixp,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/LEFT]
    [LEFT]cfg80211              178528  2 rt2x00lib,mac80211[/LEFT]
    [LEFT]soundcore              12680  1 snd[/LEFT]
    [LEFT]i2c_piix4              13303  0 [/LEFT]
    [LEFT]shpchp                 37297  0 [/LEFT]
    [LEFT]eeprom_93cx6           12725  1 rt2500pci[/LEFT]
    [LEFT]snd_page_alloc         18529  2 snd_atiixp,snd_pcm[/LEFT]
    [LEFT]ppdev                  17113  0 [/LEFT]
    [LEFT]k8temp                 13016  0 [/LEFT]
    [LEFT]parport_pc             36959  1 [/LEFT]
    [LEFT]lp                     17825  0 [/LEFT]
    [LEFT]parport                46458  3 ppdev,parport_pc,lp[/LEFT]
    [LEFT]usbhid                 46956  0 [/LEFT]
    [LEFT]8139too                32086  0 [/LEFT]
    [LEFT]firewire_ohci          40370  0 [/LEFT]
    [LEFT]firewire_core          62646  1 firewire_ohci[/LEFT]
    [LEFT]usb_storage            53538  1 [/LEFT]
    [LEFT]hid                    91020  1 usbhid[/LEFT]
    [LEFT]uas                    17996  0 [/LEFT]
    [LEFT]crc_itu_t              12707  1 firewire_core[/LEFT]
    [LEFT]sata_via               13760  2 [/LEFT]
    [LEFT]8139cp                 27218  0 [/LEFT]
    [LEFT]pata_atiixp            13165  0 [/LEFT]
    [LEFT]brandon@brandon-xubuntu:~$ cat /var/lib/NetworkManager/NetworkManager.state[/LEFT]
    [LEFT][/LEFT]
    [LEFT][main][/LEFT]
    [LEFT]NetworkingEnabled=true[/LEFT]
    [LEFT]WirelessEnabled=true[/LEFT]
    [LEFT]WWANEnabled=true[/LEFT]
    [LEFT]brandon@brandon-xubuntu:~$ [/LEFT]
    [LEFT][/LEFT]

---

### Post by Toz on 2011-06-04
Open a terminal window and type in:```
sudo iwconfig wlan0 rate 54M 
```(enter your password when prompted). Does this make the connection faster?

Do you have the original windows cd for the wireless card that you have inside the computer? Do you dual-boot with Windows?

---

