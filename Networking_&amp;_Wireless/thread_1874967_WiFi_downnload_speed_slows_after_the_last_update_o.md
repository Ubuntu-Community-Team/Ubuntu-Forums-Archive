---
title: "WiFi downnload speed slows after the last update of 11.10"
date: 2011-11-04
forum: Networking &amp; Wireless
---

### Post by meward on 2011-11-04
After last ordinary updating of Ubuntu 11.10 download internet speed on my stationary PC slows down permanently. According to speedtest.net ping stays approximately equal to 50 ms and upload speed stays equal to ~0.8 Mbps (it's as always). But download speed has now fallen from 1.8 Mbps in normal mode to 0.09 Mbps now. And it continues falling down. However download speed is ok in Windows XP that is installed at the same PC. Everything was fine even in Ubuntu 11.10 before last update.

I am using wifi to access to the router in which adsl cable is plugged (no one more is using it now). My wifi network controller Asus WL-138G V2 has no native support in Ubuntu so i used official manual ([https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)) to make it work in 11.04. Here are some command returns in terminal:

```
~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: ATI Technologies Inc RV730XT [Radeon HD 4670]
01:00.1 Audio device: ATI Technologies Inc RV710/730
03:00.0 Audio device: Creative Labs X-Fi Titanium series [EMU20k2] (rev 04)
04:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
**06:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)**
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
``````
~$ lspci -vnnd 14e4:4318
06:00.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: ASUSTeK Computer Inc. WL-138G v2 / WL-138gE / WL-100gE [1043:100f]
    Flags: bus master, fast devsel, latency 32, IRQ 20
    Memory at eb000000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
``````
~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:d0:8e:7b:81
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:b000(size=256) memory:ec010000-ec010fff memory:ec000000-ec00ffff memory:ec020000-ec02ffff
  *-network:0
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:20 memory:eb000000-eb001fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth1
       version: 10
       serial: 00:80:48:31:5f:19
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 ioport:c000(size=256) memory:eb002000-eb0020ff memory:cff00000-cff0ffff
  [B]*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:15:2d:d7:2a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic-pae firmware=410.2160 ip=192.168.1.2 link=yes multicast=yes wireless=IEEE 802.11bg[/B]
```If you assume a trouble with power management:

```
~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"PrivateNet"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:60:16:D4:C1   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:35  Invalid misc:3   Missed beacon:0
```And maybe should be useful:

```
~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
xt_limit               12541  8 
xt_tcpudp              12531  7 
ipt_LOG                12783  8 
ipt_MASQUERADE         12663  0 
xt_DSCP                12549  0 
ipt_REJECT             12512  1 
nf_conntrack_irc       13138  0 
nf_conntrack_ftp       13183  0 
xt_state               12514  6 
binfmt_misc            17292  1 
iptable_nat            13016  0 
nf_nat                 24958  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19084  9 iptable_nat,nf_nat
nf_conntrack           70103  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
iptable_mangle         12646  0 
iptable_filter         12706  1 
ip_tables              18106  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               21975  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
vesafb                 13489  1 
arc4                   12473  2 
joydev                 17393  0 
fglrx                2595570  216 
b43                   318816  0 
snd_ctxfi              85448  2 
mac80211              272785  1 b43
snd_pcm                80468  1 snd_ctxfi
snd_timer              28932  1 snd_pcm
cfg80211              172392  2 b43,mac80211
snd                    55902  7 snd_ctxfi,snd_pcm,snd_timer
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_ctxfi,snd_pcm
ppdev                  12849  0 
parport_pc             32114  1 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
8139too                23283  0 
hid                    77367  1 usbhid
8139cp                 26762  0 
pata_jmicron           12651  0 
ssb                    50682  1 b43
r8169                  47200  0 
```What should i check or repair?

---

### Post by meward on 2011-11-04
Sorry for flooding. I couldn't read fast. My problem is solved with this advice [http://ubuntuforums.org/showpost.php?p=11379397&postcount=481](http://ubuntuforums.org/showpost.php?p=11379397&postcount=481)

---

