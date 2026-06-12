---
title: "Another Atheros wireless problem on Ubuntu 12.04 LTS"
date: 2012-08-09
forum: Networking &amp; Wireless
---

### Post by Avisek003 on 2012-08-09
Hi,
Ive installed Ubuntu 12.04LTS on my Asus laptop, and after installation the 'Wireless network disconnected' is always grayed out. Ive tried out some of the solutions offered in previous posts like 

```
sudo ifconfig wlan0 down 
sudo rmmod -f ath9k 
sudo modprobe ath9k nohwcrypt=1 
sudo ifconfig wlan0 up
```


and some others, but they havent worked. Im posting some of the info I can get from my machine, please help me out if you can, if you need any other information I'll post it

1. Model : ASUS K53S

2. ```
lspci -nn | grep 'Atheros'
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

```3. ```
ifconfig
eth0      Link encap:Ethernet  HWaddr 54:04:a6:2e:ef:19  
          inet addr:10.10.34.195  Bcast:10.10.34.255  Mask:255.255.255.192
          inet6 addr: fe80::5604:a6ff:fe2e:ef19/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14037618 (14.0 MB)  TX bytes:1802239 (1.8 MB)
          Interrupt:50 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4906 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4906 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:579579 (579.5 KB)  TX bytes:579579 (579.5 KB)

wlan0     Link encap:Ethernet  HWaddr 74:2f:68:f5:e8:ac  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```4.  ```
iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

```5.  ```
lsmod | grep 'ath9k'
ath9k                 132390  0 
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath

```6. ```
sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 74:2f:68:f5:e8:ac
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-23-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:ddc00000-ddc0ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 06
       serial: 54:04:a6:2e:ef:19
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=10.10.34.195 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:50 ioport:9000(size=256) memory:d2104000-d2104fff memory:d2100000-d2103fff

```7. ```
iwlist scan
lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.

```8. ```
lsb_release -d
Description:    Ubuntu 12.04 LTS

```9. ```
uname -mr
3.2.0-23-generic x86_64

```10. [CODEsudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
][/CODE]

11. ```
dmesg | grep wlan0
[   14.941501] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.945452] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   38.986860] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   53.979935] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  363.226094] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  363.229571] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```12. ```
dmesg | egrep 'ath|firm'
[   13.756159] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.756172] ath9k 0000:03:00.0: setting latency timer to 64
[   13.806760] ath: EEPROM regdomain: 0x60
[   13.806762] ath: EEPROM indicates we should expect a direct regpair map
[   13.806764] ath: Country alpha2 being used: 00
[   13.806765] ath: Regpair used: 0x60
[   13.809859] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   13.810221] Registered led device: ath9k-phy0
[   14.946357] type=1400 audit(1344540674.652:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=847 comm="apparmor_parser"
[   14.946799] type=1400 audit(1344540674.652:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=847 comm="apparmor_parser"
[   33.477822] type=1400 audit(1344540693.204:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1608 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  341.886746] ath9k 0000:03:00.0: PCI INT A disabled
[  341.886791] ath9k: Driver unloaded
[  363.116510] ath9k 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  363.116528] ath9k 0000:03:00.0: setting latency timer to 64
[  363.166845] ath: EEPROM regdomain: 0x60
[  363.166851] ath: EEPROM indicates we should expect a direct regpair map
[  363.166858] ath: Country alpha2 being used: 00
[  363.166862] ath: Regpair used: 0x60
[  363.169271] ieee80211 phy1: Selected rate control algorithm 'ath9k_rate_control'
[  363.170485] Registered led device: ath9k-phy1

```13. ```
rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```14. Posting the wireless part - ```
nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        74:2F:68:F5:E8:AC

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


```15. ```
 lspci -nn | grep -e 0280 -e 0200
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)

```16. ```
 lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 004: ID 058f:a014 Alcor Micro Corp. 

```Any help is appreciated :) thank you in advance!

---

### Post by gordintoronto on 2012-08-09
That adapter should "just work." Did you try right-clicking on the network icon and select "edit connections"?

If it doesn't just work, you might look at:
[https://bbs.archlinux.org/viewtopic.php?pid=1050263](https://bbs.archlinux.org/viewtopic.php?pid=1050263)

---

### Post by Avisek003 on 2012-08-10
No... in edit connections i get to see an option to configure my wired connections, even if the internet wire isnt plugged into my machine, but under wireless its empty. so i added a new wireless connection, gave the ips, ssids, encryption to wpa2 personal, the password, but it still doesnt work, it shows wireless connection disconnected, and its greyed out

---

### Post by 666ABEL999 on 2012-09-24
friend know the problem you have is that the physical switch is disabling the wifi I have the same problem and that I am looking for forgiveness if you do not help much but that happens to me too

---

