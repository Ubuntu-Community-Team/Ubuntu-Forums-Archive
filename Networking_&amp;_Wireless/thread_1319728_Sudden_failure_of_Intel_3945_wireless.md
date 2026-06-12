---
title: "Sudden failure of Intel 3945 wireless"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by FokkerCharlie on 2009-11-08
Hello!

Today, after upgrading the memory on my Acer 5920 laptop, the wireless suddenly stopped working.  I've also installed (and subsequently uninstalled) some bluetooth packages using Synaptic.

Anyway, some info:

lspci:

```
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:c8:41:9f  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fec8:419f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:900 errors:0 dropped:0 overruns:0 frame:0
          TX packets:871 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:874631 (874.6 KB)  TX bytes:139093 (139.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9792 (9.7 KB)  TX bytes:9792 (9.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:69:1e:97  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-69-1E-97-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```
~$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"CharlesNet"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
~$ lsmod | grep "iwl"
iwl3945                94212  0 
iwlcore               129024  1 iwl3945
lbm_cw_mac80211       259000  2 iwl3945,iwlcore
lbm_cw_cfg80211        85048  3 iwl3945,iwlcore,lbm_cw_mac80211
led_class              13064  3 iwl3945,iwlcore,acer_wmi

```

dmesg:
```
[  106.189647] iwl3945 0000:06:00.0: firmware: requesting lbm-iwlwifi-3945-2.ucode
[  106.517414] iwl3945 0000:06:00.0: loaded firmware version 15.28.2.8
[  106.564179] Registered led device: iwl-phy0::radio
[  106.564358] Registered led device: iwl-phy0::assoc
[  106.565699] Registered led device: iwl-phy0::RX
[  106.565722] Registered led device: iwl-phy0::TX
[  106.581513] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  107.750412] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  107.750415] tg3: eth0: Flow control is on for TX and on for RX.
[  107.751038] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  118.472056] eth0: no IPv6 routers present
[  144.440477] wlan0: authenticate with AP ffff88013ccc8ac0
[  144.641034] wlan0: authenticate with AP ffff88013ccc8ac0
[  144.641116] iwl3945 0000:06:00.0: Microcode SW error detected. Restarting 0x82000008.
[  144.641128] iwl3945 0000:06:00.0: Error Reply type 0x00000005 cmd REPLY_PHY_CALIBRATION_CMD (0xB0) seq 0x013A ser 0x004E0000
[  144.686685] Registered led device: iwl-phy0::radio
[  144.686714] Registered led device: iwl-phy0::assoc
[  144.686738] Registered led device: iwl-phy0::RX
[  144.686762] Registered led device: iwl-phy0::TX
[  144.844062] wlan0: authenticate with AP ffff88013ccc8ac0
[  145.044060] wlan0: authentication with AP ffff88013ccc8ac0 timed out
[  154.944478] iwl3945 0000:06:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
[  155.445199] iwl3945 0000:06:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
[  160.444111] iwl3945 0000:06:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
[  160.945026] iwl3945 0000:06:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
[  165.949070] iwl3945 0000:06:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
[  166.449109] iwl3945 0000:06:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
[  171.449142] iwl3945 0000:06:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
[  171.948203] iwl3945 0000:06:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.
[  176.952256] iwl3945 0000:06:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
[  177.452121] iwl3945 0000:06:00.0: Error sending REPLY_TX_PWR_TABLE_CMD: time out after 500ms.

```

```
~$ sudo lshw -C network
[sudo] password for charlie: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:69:1e:97
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:24:c8:41:9f
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5787m-v3.23 ip=192.168.1.5 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

```
~$ iwlist wlan0 scan
wlan0     No scan results

```

```
~$ lsb_release -d
Description:	Ubuntu 9.04
```

```
~$ uname -mr
2.6.28-15-generic x86_64
```
(I have fallen back to this kernel after having problems with the current one- no difference observed.

```
~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
```

On logging in, All appears normal, although network manager shows that it's trying to connect to my network, gives up after 30 seconds or so, and asks me for my password (WPA).  Then it tries again, with the same effect.

It's all very strange.  Earlier today, I was perfectly able to connect to my wireless router.  When I boot into Vista, it also works fine.

Please help!

Charlie

---

