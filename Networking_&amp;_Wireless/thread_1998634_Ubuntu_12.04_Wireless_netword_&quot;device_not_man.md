---
title: "Ubuntu 12.04 Wireless netword &quot;device not managed&quot;"
date: 2012-06-07
forum: Networking &amp; Wireless
---

### Post by Midnight22 on 2012-06-07
Hi,

I recently installed Ubuntu 12.04 on a new pc and the wireless worked fine out-of-the-box. However, after a recent reboot it stopped working, saying "device not managed". I have a D-Link DWA547 wireless card with an Atheros Communications Inc. AR922X chipset.

I have tried to run wirelesGUI.sh ([http://ubuntuforums.org/showthread.php?p=11103088) and](http://ubuntuforums.org/showthread.php?p=11103088) and) to install the latest ath9k drivers, but no success.

Here is some more info:

```
iwconfig
```  
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

```
lspci -nn | grep 0280
```
03:02.0 Network controller [0280]: Atheros Communications Inc. AR922X Wireless Network Adapter [168c:0029] (rev 01)

```
lspci
```
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation Panther Point KT Controller (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation Panther Point 4 port SATA Controller [IDE mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
00:1f.5 IDE interface: Intel Corporation Panther Point 2 port SATA Controller [IDE mode] (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:02.0 Network controller: Atheros Communications Inc. AR922X Wireless Network Adapter (rev 01)

```
sudo lshw -C network
```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 90:2b:34:1c:89:bf
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.10.106 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network DISABLED
       description: Wireless interface
       product: AR922X Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: wlan0
       version: 01
       serial: 14:d6:4d:08:fa:aa
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-24-generic-pae firmware=N/A latency=168 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f7c00000-f7c0ffff

```
rfkill list all
```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


Thank you for your help! I am a relatively inxeperienced Ubuntu user, so please keep the instructions simple if you can ;)

---

### Post by chili555 on 2012-06-07
> *-network [COLOR="Red"]DISABLED[/COLOR]
description: Wireless interface
product: AR922X Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 2
bus info: pci@0000:03:02.0
logical name: wlan0One wonders why it's disabled. Usually, rfkill is the culprit, but:> 0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: noWere those all the listings? No bluetooth, acer-wireless, hp-wmi, etc.?

Network Manager is supposed to default to wired if you have it, and you do:> duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 [COLOR="Red"]ip=192.168.10.106[/COLOR] latency=0 link=yes multicast=yes port=MII speed=100Mbit/sIf you detach the ethernet cable and wait a few moments for NM to notice the change in state, and again run:```
sudo lshw -C network
```Does it still show DISABLED?

Does it scan?```
sudo iwlist wlan0 scan
```Finally, are there any interesting clues here?```
dmesg | grep ath
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

Any errors, warnings, etc. are valuable clues. Please note and post them.

---

### Post by Midnight22 on 2012-06-07
Hi  chili555

> Were those all the listings? No bluetooth, acer-wireless, hp-wmi, etc.?

Yes, that was all the output I got.

When I detach the cable and run sudo lshw -C network again, it still tells me that the network is disabled:

*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 90:2b:34:1c:89:bf
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network DISABLED
       description: Wireless interface
       product: AR922X Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: wlan0
       version: 01
       serial: 14:d6:4d:08:fa:aa
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-24-generic-pae firmware=N/A latency=168 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f7c00000-f7c0ffff

When I try to scan it gives me the following message:
wlan0     Interface doesn't support scanning : Network is down

Finally, dmesg | grep ath gives me the following output:
 
[   15.623939] ath9k 0000:03:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   17.186514] ath: EEPROM regdomain: 0x30
[   17.186515] ath: EEPROM indicates we should expect a direct regpair map
[   17.186517] ath: Country alpha2 being used: AM
[   17.186518] ath: Regpair used: 0x30
[   17.190921] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   17.191255] Registered led device: ath9k-phy0
[   17.865497] type=1400 audit(1339080607.927:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1004 comm="apparmor_parser"

Any ideas as to what might be the problem?

---

### Post by chili555 on 2012-06-07
> Any ideas as to what might be the problem?Not yet. Please run:```
sudo ifconfig wlan0 up > midnight.txt
dmesg >> midnight.txt
iwconfig >> midnight.txt
```Find the document midnight.txt in your user directory and paste it here and give me the link in your reply.

[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Your readings look pretty solid, actually.

---

### Post by Midnight22 on 2012-06-07
Hi, the link is [http://paste.ubuntu.com/1028879/](http://paste.ubuntu.com/1028879/)

---

### Post by chili555 on 2012-06-07
Your paste looks remarkably perfect. Please do:```
sudo nano /etc/NetworkManager/NetworkManager.conf
```If you don't have the text editor nano, use gedit, leafpad, kate, vim or any text editor. Change the line managed=false to managed=true. Proofread, save and close the text editor. Now do:```
sudo service network-manager restart
```Now, please do:```
sudo nano /etc/network/interfaces
```Make sure it contains only:```
auto lo
iface lo inet loopback
```If there are any other entries in there, please remove them. Proofread, save and close the text editor. If you make any changes, restart Network Manager:```
sudo service network-manager restart
```Now does it still show as 'device not managed?'

---

### Post by Midnight22 on 2012-06-08
Thank you so much! That worked perfectly :)
There was extra pppoe code in Interfaces. After I deleted it, the wireless works perfectly again. Thanks.

---

### Post by chili555 on 2012-06-08
Awesome! Glad it's working. Please use thread tools at the top to mark Solved.

---

### Post by mdacova on 2012-08-07
> **chili555 said:**
> Awesome! Glad it's working. Please use thread tools at the top to mark Solved.

thank you worked for me also

---

### Post by michelepolo on 2012-09-17
> **mdacova said:**
> thank you worked for me also

for me too, i was wondering why the eth0 was perfectly working within the installation process, and not during normal use!
thanks

---

### Post by mrmacedonian on 2012-12-17
I've had this problem randomly on various machines with the exception that it was the wired (eth0) that was coming up "not managed." Ubuntu was showing no wired connection active yet the internet worked fine. this was annoying more so than a serious problem but I stumbled upon this post and now its fixed on both previously-plagued machines! thank you! :D

---

### Post by Ertai87 on 2013-04-06
Much obliged =D

---

### Post by solidpython on 2013-10-11
I have the same problem but my *-network is not DISABLED, im now on 13.04. it works fine before but now its not working even i can detect my wifi, it cant connect now.

---

### Post by chili555 on 2013-10-11
> **solidpython said:**
> I have the same problem but my *-network is not DISABLED, im now on 13.04. it works fine before but now its not working even i can detect my wifi, it cant connect now.Why is it disabled? What does this tell us?```
dmesg | grep wlan
rfkill list all
```

---

### Post by solidpython on 2013-10-12
Thanks [**[COLOR=#000000]chili555[/COLOR]**]("http://ubuntuforums.org/member.php?u=35909") its working now. Im noob sorry, the problem is DHCP is not working on my end, so i decided to manually enter my ip and viola! its now working! 
its weird because I remember when I was first install this on my machine and it detects instantly and all i need is to input my wifi password. But thanks again to this forum i learned alot from this!!

Update:

It didnt work again sir. :( it disconnects.

**dmesg | grep wlan**


> [   25.735949] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.739296] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.677065] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   26.677532] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   28.724502] wlan0: authenticate with 58:6d:8f:c7:7f:4a
[   28.736945] wlan0: send auth to 58:6d:8f:c7:7f:4a (try 1/3)
[   28.738907] wlan0: authenticated
[   28.739848] wlan0: associate with 58:6d:8f:c7:7f:4a (try 1/3)
[   28.743440] wlan0: RX AssocResp from 58:6d:8f:c7:7f:4a (capab=0x411 status=0 aid=1)
[   28.743510] wlan0: associated
[   28.743532] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.627927] wlan1: authenticate with 58:6d:8f:c7:7f:4a
[   29.694223] wlan1: send auth to 58:6d:8f:c7:7f:4a (try 1/3)
[   29.695700] wlan1: authenticated
[   29.698780] wlan1: associate with 58:6d:8f:c7:7f:4a (try 1/3)
[   29.701704] wlan1: RX AssocResp from 58:6d:8f:c7:7f:4a (capab=0x411 status=0 aid=2)
[   29.709423] wlan1: associated
[   29.709476] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1574.832063] wlan0: deauthenticating from 58:6d:8f:c7:7f:4a by local choice (reason=3)
[ 1575.524725] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1578.365647] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1579.467297] wlan0: authenticate with 58:6d:8f:c7:7f:4a
[ 1579.486326] wlan0: send auth to 58:6d:8f:c7:7f:4a (try 1/3)
[ 1579.488291] wlan0: authenticated
[ 1579.492078] wlan0: associate with 58:6d:8f:c7:7f:4a (try 1/3)
[ 1579.495680] wlan0: RX AssocResp from 58:6d:8f:c7:7f:4a (capab=0x411 status=0 aid=1)
[ 1579.495734] wlan0: associated
[ 1579.495767] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1586.379140] wlan1: deauthenticating from 58:6d:8f:c7:7f:4a by local choice (reason=3)
[ 1604.462224] wlan0: deauthenticating from 58:6d:8f:c7:7f:4a by local choice (reason=3)
[ 1615.436182] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1615.439486] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1617.523430] wlan0: authenticate with 58:6d:8f:c7:7f:4a
[ 1617.536401] wlan0: send auth to 58:6d:8f:c7:7f:4a (try 1/3)
[ 1617.538395] wlan0: authenticated
[ 1617.542313] wlan0: associate with 58:6d:8f:c7:7f:4a (try 1/3)
[ 1617.545937] wlan0: RX AssocResp from 58:6d:8f:c7:7f:4a (capab=0x411 status=0 aid=1)
[ 1617.546012] wlan0: associated
[ 1617.546075] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1683.789787] wlan0: deauthenticating from 58:6d:8f:c7:7f:4a by local choice (reason=3)
[ 1693.310783] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1693.314329] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1695.378297] wlan0: authenticate with 58:6d:8f:c7:7f:4a
[ 1695.390656] wlan0: send auth to 58:6d:8f:c7:7f:4a (try 1/3)
[ 1695.397695] wlan0: authenticated
[ 1695.400720] wlan0: associate with 58:6d:8f:c7:7f:4a (try 1/3)
[ 1695.407412] wlan0: RX AssocResp from 58:6d:8f:c7:7f:4a (capab=0x411 status=0 aid=1)
[ 1695.407501] wlan0: associated
[ 1695.407523] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1766.908340] wlan0: deauthenticating from 58:6d:8f:c7:7f:4a by local choice (reason=3)
[ 1772.437289] wlan0: authenticate with 58:6d:8f:c7:7f:4a
[ 1772.449803] wlan0: send auth to 58:6d:8f:c7:7f:4a (try 1/3)
[ 1772.451752] wlan0: authenticated
[ 1772.451968] wlan0: associate with 58:6d:8f:c7:7f:4a (try 1/3)
[ 1772.455611] wlan0: RX AssocResp from 58:6d:8f:c7:7f:4a (capab=0x411 status=0 aid=1)
[ 1772.455659] wlan0: associated
[ 1806.514832] wlan0: deauthenticating from 58:6d:8f:c7:7f:4a by local choice (reason=3)
[ 1811.659576] wlan1: authenticate with 58:6d:8f:c7:7f:4a
[ 1811.718842] wlan1: send auth to 58:6d:8f:c7:7f:4a (try 1/3)
[ 1811.720390] wlan1: authenticated
[ 1811.724802] wlan1: associate with 58:6d:8f:c7:7f:4a (try 1/3)
[ 1811.727927] wlan1: RX AssocResp from 58:6d:8f:c7:7f:4a (capab=0x411 status=0 aid=1)
[ 1811.735587] wlan1: associated
[ 1852.785204] wlan1: deauthenticating from 58:6d:8f:c7:7f:4a by local choice (reason=3)
[ 1872.459496] wlan1: authenticate with 58:6d:8f:c7:7f:4a
[ 1872.523476] wlan1: send auth to 58:6d:8f:c7:7f:4a (try 1/3)
[ 1872.525031] wlan1: authenticated
[ 1872.525865] wlan1: associate with 58:6d:8f:c7:7f:4a (try 1/3)
[ 1872.528897] wlan1: RX AssocResp from 58:6d:8f:c7:7f:4a (capab=0x411 status=0 aid=1)
[ 1872.536738] wlan1: associated
[ 2188.937195] wlan1: deauthenticating from 58:6d:8f:c7:7f:4a by local choice (reason=3)
[ 2192.946221] wlan0: authenticate with 58:6d:8f:c7:7f:4a
[ 2192.958435] wlan0: send auth to 58:6d:8f:c7:7f:4a (try 1/3)
[ 2192.969837] wlan0: authenticated
[ 2192.973171] wlan0: associate with 58:6d:8f:c7:7f:4a (try 1/3)
[ 2192.976807] wlan0: RX AssocResp from 58:6d:8f:c7:7f:4a (capab=0x411 status=0 aid=1)
[ 2192.976934] wlan0: associated
[ 2238.767493] wlan0: deauthenticating from 58:6d:8f:c7:7f:4a by local choice (reason=3)
[ 2242.599400] wlan0: authenticate with 58:6d:8f:c7:7f:4a
[ 2242.612789] wlan0: send auth to 58:6d:8f:c7:7f:4a (try 1/3)
[ 2242.614860] wlan0: authenticated
[ 2242.618338] wlan0: associate with 58:6d:8f:c7:7f:4a (try 1/3)
[ 2242.622116] wlan0: RX AssocResp from 58:6d:8f:c7:7f:4a (capab=0x411 status=0 aid=1)
[ 2242.622162] wlan0: associated
[ 2287.710153] wlan0: deauthenticating from 58:6d:8f:c7:7f:4a by local choice (reason=3)
[ 2293.743392] wlan0: authenticate with 58:6d:8f:c7:7f:4a
[ 2293.756034] wlan0: send auth to 58:6d:8f:c7:7f:4a (try 1/3)
[ 2293.757989] wlan0: authenticated
[ 2293.762084] wlan0: associate with 58:6d:8f:c7:7f:4a (try 1/3)
[ 2293.765736] wlan0: RX AssocResp from 58:6d:8f:c7:7f:4a (capab=0x411 status=0 aid=1)
[ 2293.765817] wlan0: associated
[ 2339.654680] wlan0: deauthenticating from 58:6d:8f:c7:7f:4a by local choice (reason=3)
[ 2345.701489] wlan0: authenticate with 58:6d:8f:c7:7f:4a
[ 2345.714331] wlan0: send auth to 58:6d:8f:c7:7f:4a (try 1/3)
[ 2345.716318] wlan0: authenticated
[ 2345.716981] wlan0: associate with 58:6d:8f:c7:7f:4a (try 1/3)
[ 2345.720753] wlan0: RX AssocResp from 58:6d:8f:c7:7f:4a (capab=0x411 status=0 aid=1)
[ 2345.720847] wlan0: associated
[ 2366.923981] wlan0: deauthenticating from 58:6d:8f:c7:7f:4a by local choice (reason=3)
[ 2380.787304] wlan0: authenticate with 58:6d:8f:c7:7f:4a
[ 2380.800181] wlan0: send auth to 58:6d:8f:c7:7f:4a (try 1/3)
[ 2380.802412] wlan0: authenticated
[ 2380.806383] wlan0: associate with 58:6d:8f:c7:7f:4a (try 1/3)
[ 2380.810065] wlan0: RX AssocResp from 58:6d:8f:c7:7f:4a (capab=0x411 status=0 aid=1)
[ 2380.810154] wlan0: associated
[ 2998.754614] wlan0: deauthenticating from 58:6d:8f:c7:7f:4a by local choice (reason=3)
[ 3002.727348] wlan0: authenticate with 58:6d:8f:c7:7f:4a
[ 3002.740241] wlan0: send auth to 58:6d:8f:c7:7f:4a (try 1/3)
[ 3002.742222] wlan0: authenticated
[ 3002.742714] wlan0: associate with 58:6d:8f:c7:7f:4a (try 1/3)
[ 3002.746336] wlan0: RX AssocResp from 58:6d:8f:c7:7f:4a (capab=0x411 status=0 aid=1)
[ 3002.746392] wlan0: associated
[ 3055.672826] wlan0: deauthenticating from 58:6d:8f:c7:7f:4a by local choice (reason=3)
[ 3061.690368] wlan0: authenticate with 58:6d:8f:c7:7f:4a
[ 3061.703568] wlan0: send auth to 58:6d:8f:c7:7f:4a (try 1/3)
[ 3061.705598] wlan0: authenticated
[ 3061.709866] wlan0: associate with 58:6d:8f:c7:7f:4a (try 1/3)
[ 3061.713504] wlan0: RX AssocResp from 58:6d:8f:c7:7f:4a (capab=0x411 status=0 aid=1)
[ 3061.713594] wlan0: associated
[ 3112.924945] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3112.926034] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 3115.892248] wlan1: authenticate with 58:6d:8f:c7:7f:4a
[ 3115.957781] wlan1: send auth to 58:6d:8f:c7:7f:4a (try 1/3)
[ 3115.959318] wlan1: authenticated
[ 3115.962246] wlan1: associate with 58:6d:8f:c7:7f:4a (try 1/3)
[ 3115.965185] wlan1: RX AssocResp from 58:6d:8f:c7:7f:4a (capab=0x411 status=0 aid=2)
[ 3115.972650] wlan1: associated
[ 3115.972707] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 3142.546351] wlan1: deauthenticating from 58:6d:8f:c7:7f:4a by local choice (reason=3)
[ 3157.853494] wlan1: authenticate with 58:6d:8f:c7:7f:4a
[ 3157.913662] wlan1: send auth to 58:6d:8f:c7:7f:4a (try 1/3)
[ 3157.916209] wlan1: authenticated
[ 3157.920135] wlan1: associate with 58:6d:8f:c7:7f:4a (try 1/3)
[ 3157.923179] wlan1: RX AssocResp from 58:6d:8f:c7:7f:4a (capab=0x411 status=0 aid=2)
[ 3157.930898] wlan1: associated
[ 3158.664603] wlan0: deauthenticating from 58:6d:8f:c7:7f:4a by local choice (reason=3)
[ 3407.220613] wlan1: deauthenticating from 58:6d:8f:c7:7f:4a by local choice (reason=3)

**rfkill list all**
> 1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
6: phy3: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by dou3516 on 2013-11-19
It does work for me! Thanks! Ths to chili555!

---

### Post by wilbury2 on 2014-09-14
Many, many thanks! You helped very well. :KS

---

### Post by nguyenquocuy-1102 on 2014-11-14
> **chili555 said:**
> Your paste looks remarkably perfect. Please do:```
sudo nano /etc/NetworkManager/NetworkManager.conf
```If you don't have the text editor nano, use gedit, leafpad, kate, vim or any text editor. Change the line managed=false to managed=true. Proofread, save and close the text editor. Now do:```
sudo service network-manager restart
```Now, please do:```
sudo nano /etc/network/interfaces
```Make sure it contains only:```
auto lo
iface lo inet loopback
```If there are any other entries in there, please remove them. Proofread, save and close the text editor. If you make any changes, restart Network Manager:```
sudo service network-manager restart
```Now does it still show as 'device not managed?'
I just register to say THANKS! YOU SAVED MY DAY!

---

### Post by miker_alpha on 2015-05-12
Thanks, worked for me; fixed eth0 "device not managed" on 14.04

---

