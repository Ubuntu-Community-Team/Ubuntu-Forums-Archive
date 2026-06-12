---
title: "Unable to connect to Internet through wireless network"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by jayeshvani on 2010-05-21
I am unable to connect to internet using my wifi network. Though I can share folders on network. Here are the details:

HP Pavalion laptop - DV6149us

lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)

02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller

05:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)

05:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)

05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)

05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)



lsusb

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



ifconfig

eth0      Link encap:Ethernet  HWaddr 00:16:36:97:ae:9d  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:4 errors:0 dropped:0 overruns:0 frame:0

          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)



wlan0     Link encap:Ethernet  HWaddr 00:18:de:31:48:e2  

          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::218:deff:fe31:48e2/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:653 errors:0 dropped:0 overruns:0 frame:0

          TX packets:682 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:58140 (58.1 KB)  TX bytes:76696 (76.6 KB)



wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-31-48-E2-33-31-00-00-00-00-00-00-00-00  

          UP RUNNING  MTU:0  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wmaster0  no wireless extensions.



wlan0     IEEE 802.11abg  ESSID:"mtnl"  

          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1B:57:E6:8F:31   

          Bit Rate=54 Mb/s   Tx-Power=15 dBm   

          Retry  long limit:7   RTS thr:off   Fragment thr:off

          Power Management:off

          Link Quality=70/70  Signal level=-19 dBm  Noise level=-127 dBm

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


vboxnet0  no wireless extensions.



lsmod

Module                  Size  Used by

vboxnetadp              7296  0 

vboxnetflt             14344  0 

vboxdrv               176360  2 vboxnetadp,vboxnetflt

iwl3945                77372  0 

iwlcore               112796  1 iwl3945

mac80211              181140  2 iwl3945,iwlcore

sdhci_pci               7100  0 

cfg80211               93052  3 iwl3945,iwlcore,mac80211

lp                      8964  0 

ohci1394               29900  0 

ieee1394               86596  1 ohci1394

e100                   32420  0 


dmesg | grep "wlan0"

[   18.594232] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[   27.036584] wlan0: authenticate with AP 00:1b:57:e6:8f:31

[   27.038750] wlan0: authenticated

[   27.038756] wlan0: associate with AP 00:1b:57:e6:8f:31

[   27.041667] wlan0: RX AssocResp from 00:1b:57:e6:8f:31 (capab=0x411 status=0 aid=2)

[   27.041672] wlan0: associated

[   27.048477] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[   37.140022] wlan0: no IPv6 routers present

[  135.749525] wlan0: disassociating by local choice (reason=3)

[  135.801628] wlan0: deauthenticating by local choice (reason=3)

[  152.034018] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[  157.068979] wlan0: authenticate with AP 00:1b:57:e6:8f:31

[  157.071149] wlan0: authenticated

[  157.071155] wlan0: associate with AP 00:1b:57:e6:8f:31

[  157.073657] wlan0: RX AssocResp from 00:1b:57:e6:8f:31 (capab=0x411 status=0 aid=2)

[  157.073663] wlan0: associated

[  157.075525] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[  167.848130] wlan0: no IPv6 routers present

[  231.358409] wlan0: disassociating by local choice (reason=3)

[  243.089811] wlan0: authenticate with AP 00:1b:57:e6:8f:31

[  243.091951] wlan0: authenticated

[  243.091956] wlan0: associate with AP 00:1b:57:e6:8f:31

[  243.094512] wlan0: RX AssocResp from 00:1b:57:e6:8f:31 (capab=0x411 status=0 aid=2)

[  243.094518] wlan0: associated

[  262.960128] wlan0: deauthenticating by local choice (reason=3)

[  266.896936] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[  271.934061] wlan0: authenticate with AP 00:1b:57:e6:8f:31

[  271.936542] wlan0: authenticated

[  271.936549] wlan0: associate with AP 00:1b:57:e6:8f:31

[  271.939357] wlan0: RX AssocResp from 00:1b:57:e6:8f:31 (capab=0x411 status=0 aid=2)

[  271.939363] wlan0: associated

[  271.942288] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[  282.720108] wlan0: no IPv6 routers present

[ 1608.136684] wlan0: disassociating by local choice (reason=3)

[ 1658.609897] wlan0: authenticate with AP 00:1b:57:e6:8f:31

[ 1658.612058] wlan0: authenticated

[ 1658.612064] wlan0: associate with AP 00:1b:57:e6:8f:31

[ 1658.614605] wlan0: RX AssocResp from 00:1b:57:e6:8f:31 (capab=0x411 status=0 aid=2)

[ 1658.614611] wlan0: associated

sudo lshw -C Network

  *-network               

       description: Wireless interface

       product: PRO/Wireless 3945ABG [Golan] Network Connection

       vendor: Intel Corporation

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: wmaster0

       version: 02

       serial: 00:18:de:31:48:e2

       width: 32 bits

       clock: 33MHz

       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless

       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.2 latency=0 multicast=yes wireless=IEEE 802.11abg

       resources: irq:27 memory:d6000000-d6000fff

  *-network

       description: Ethernet interface

       product: PRO/100 VE Network Connection

       vendor: Intel Corporation

       physical id: 8

       bus info: pci@0000:05:08.0

       logical name: eth0

       version: 02

       serial: 00:16:36:97:ae:9d

       size: 10MB/s

       capacity: 100MB/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s

       resources: irq:20 memory:d8000000-d8000fff ioport:4000(size=64)

  *-network DISABLED

       description: Ethernet interface

       physical id: 1

       logical name: vboxnet0

       serial: 0a:00:27:00:00:00

       capabilities: ethernet physical

       configuration: broadcast=yes multicast=yes



iwlist scan

lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning.
wlan0     Scan completed :

          Cell 01 - Address: 00:1B:57:E6:8F:31

                    Channel:1

                    Frequency:2.412 GHz (Channel 1)

                    Quality=70/70  Signal level=-23 dBm  

                    Encryption key:on

                    ESSID:"mtnl"

                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s

                              24 Mb/s; 36 Mb/s; 54 Mb/s

                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s

                    Mode:Master

                    Extra:tsf=000000028db79187

                    Extra: Last beacon: 61640ms ago

                    IE: Unknown: 00046D746E6C

                    IE: Unknown: 010882848B962430486C

                    IE: Unknown: 030101

                    IE: Unknown: 2A0100

                    IE: Unknown: 2F0100

                    IE: Unknown: 32040C121860

                    IE: Unknown: DD090010180201F4000000

                    IE: WPA Version 1

                        Group Cipher : TKIP

                        Pairwise Ciphers (1) : TKIP

                        Authentication Suites (1) : PSK

vboxnet0  Interface doesn't support scanning.

lsb_release -d
Description: Ubuntu 9.10

uname -mr
2.6.31-20-generic i686

sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                    [ OK ]

---

### Post by mikewhatever on 2010-05-21
May be a dns resolution issue. Could you also post the outputs of the following:

ping -c4 google.com

ping -c4 216.239.59.99

nm-tool

---

