---
title: "Intel 5100 AGN, Dell Studio XPS, Ubuntu 12.04, not working"
date: 2012-07-23
forum: Networking &amp; Wireless
---

### Post by CDCM on 2012-07-23
My laptop is a Dell Studio XPS, 1645 I believe? Wireless chip is Intel 5100 AGN.  I am new to Linux.

My wireless problem is intermittent.  Sometimes it can connect, sometimes it cannot.  When it can't, it repeatedly asks me for the wireless password.  (I have experienced the same problem when I've set the network to no security to try as well.)  It is always able to detect that the networks exist, and it attempts to connect.


**lspci / lsusb**
```
clement@ubuntu:~$ lspci | grep 'Network'
04:00.0 Network controller: Intel Corporation WiFi Link 5100

```
```
clement@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:18a0 Ricoh Co., Ltd 
Bus 003 Device 005: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 006: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 007: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick

```
**ifconfig / iwconfig**
```
wlan0     Link encap:Ethernet  HWaddr 00:22:fb:b6:e0:d8  
          inet6 addr: fe80::222:fbff:feb6:e0d8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9733 (9.7 KB)  TX bytes:6214 (6.2 KB)


wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


```

**lsmod**
```
clement@ubuntu:~$ lsmod | grep "iwlwifi"
iwlwifi               332672  0 
mac80211              506816  1 iwlwifi
cfg80211              205544  2 iwlwifi,mac80211

```
**dmesg**
```
clement@ubuntu:~$ dmesg | grep "iwlwifi"
[   39.155125] iwlwifi 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   39.155134] iwlwifi 0000:04:00.0: setting latency timer to 64
[   39.156769] iwlwifi 0000:04:00.0: pci_resource_len = 0x00002000
[   39.156772] iwlwifi 0000:04:00.0: pci_resource_base = ffffc90011098000
[   39.156775] iwlwifi 0000:04:00.0: HW Revision ID = 0x0
[   39.156856] iwlwifi 0000:04:00.0: irq 48 for MSI/MSI-X
[   39.156898] iwlwifi 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   39.156955] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   39.177946] iwlwifi 0000:04:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   39.177950] iwlwifi 0000:04:00.0: Device SKU: 0Xf0
[   39.212523] iwlwifi 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   39.255949] iwlwifi 0000:04:00.0: loaded firmware version 8.83.5.1 build 33692
[   39.870321] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   39.873373] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[   39.988790] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[   39.991765] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[ 5103.744822] iwlwifi 0000:04:00.0: RF_KILL bit toggled to disable radio.
[ 5103.744968] iwlwifi 0000:04:00.0: Not sending command - RF KILL
[ 5103.744978] iwlwifi 0000:04:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[ 5103.744987] iwlwifi 0000:04:00.0: Error clearing ASSOC_MSK on BSS (-5)
[ 5103.756046] iwlwifi 0000:04:00.0: Not sending command - RF KILL
[ 5103.756057] iwlwifi 0000:04:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
[ 5103.756065] iwlwifi 0000:04:00.0: Error clearing ASSOC_MSK on BSS (-5)
[ 5152.517992] iwlwifi 0000:04:00.0: RF_KILL bit toggled to enable radio.
[ 5153.830690] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[ 5153.833746] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[ 5407.829096] iwlwifi 0000:04:00.0: PCI INT A disabled
[ 5421.997732] iwlwifi 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 5421.997765] iwlwifi 0000:04:00.0: setting latency timer to 64
[ 5421.997817] iwlwifi 0000:04:00.0: pci_resource_len = 0x00002000
[ 5421.997819] iwlwifi 0000:04:00.0: pci_resource_base = ffffc90011098000
[ 5421.997822] iwlwifi 0000:04:00.0: HW Revision ID = 0x0
[ 5421.997954] iwlwifi 0000:04:00.0: irq 48 for MSI/MSI-X
[ 5421.998037] iwlwifi 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 5421.998134] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[ 5422.019283] iwlwifi 0000:04:00.0: device EEPROM VER=0x11f, CALIB=0x4
[ 5422.019286] iwlwifi 0000:04:00.0: Device SKU: 0Xf0
[ 5422.019313] iwlwifi 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 5422.071361] iwlwifi 0000:04:00.0: loaded firmware version 8.83.5.1 build 33692
[ 5422.104709] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[ 5422.107688] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[ 5422.220683] iwlwifi 0000:04:00.0: L1 Enabled; Disabling L0S
[ 5422.223661] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0

```
Note that **dmesg** also spews out rapidly 
```
[ 5463.096351] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5474.644008] wlan0: no IPv6 routers present
[ 5490.952658] wlan0: deauthenticating from 00:02:cf:70:bc:4a by local choice (reason=3)
[ 5494.117922] wlan0: authenticate with 00:02:cf:70:bc:4a (try 1)
[ 5494.316035] wlan0: authenticate with 00:02:cf:70:bc:4a (try 2)
[ 5494.516036] wlan0: authenticate with 00:02:cf:70:bc:4a (try 3)
[ 5494.716056] wlan0: authentication with 00:02:cf:70:bc:4a timed out
[ 5502.795607] wlan0: direct probe to 00:02:cf:70:bc:4a (try 1/3)
[ 5502.992035] wlan0: direct probe to 00:02:cf:70:bc:4a (try 2/3)
[ 5503.192052] wlan0: direct probe to 00:02:cf:70:bc:4a (try 3/3)
[ 5503.392042] wlan0: direct probe to 00:02:cf:70:bc:4a timed out
[ 5511.500912] wlan0: direct probe to 00:02:cf:70:bc:4a (try 1/3)
[ 5511.700044] wlan0: direct probe to 00:02:cf:70:bc:4a (try 2/3)
[ 5511.900042] wlan0: direct probe to 00:02:cf:70:bc:4a (try 3/3)
[ 5512.100083] wlan0: direct probe to 00:02:cf:70:bc:4a timed out
[ 5520.207280] wlan0: direct probe to 00:02:cf:70:bc:4a (try 1/3)
[ 5520.404037] wlan0: direct probe to 00:02:cf:70:bc:4a (try 2/3)
[ 5520.608039] wlan0: direct probe to 00:02:cf:70:bc:4a (try 3/3)
[ 5520.808031] wlan0: direct probe to 00:02:cf:70:bc:4a timed out
[ 5528.930438] wlan0: direct probe to 00:02:cf:70:bc:4a (try 1/3)
[ 5529.128045] wlan0: direct probe to 00:02:cf:70:bc:4a (try 2/3)
[ 5529.328106] wlan0: direct probe to 00:02:cf:70:bc:4a (try 3/3)
[ 5529.528099] wlan0: direct probe to 00:02:cf:70:bc:4a timed out
[ 5537.616597] wlan0: direct probe to 00:02:cf:70:bc:4a (try 1/3)
[ 5537.816062] wlan0: direct probe to 00:02:cf:70:bc:4a (try 2/3)
[ 5538.016124] wlan0: direct probe to 00:02:cf:70:bc:4a (try 3/3)
[ 5538.216068] wlan0: direct probe to 00:02:cf:70:bc:4a timed out
[ 5546.315203] wlan0: direct probe to 00:02:cf:70:bc:4a (try 1/3)
[ 5546.512029] wlan0: direct probe to 00:02:cf:70:bc:4a (try 2/3)
[ 5546.712180] wlan0: direct probe to 00:02:cf:70:bc:4a (try 3/3)
[ 5546.912253] wlan0: direct probe to 00:02:cf:70:bc:4a timed out
[ 5857.117424] wlan0: direct probe to 00:02:cf:70:bc:4a (try 1/3)
[ 5857.316313] wlan0: direct probe to 00:02:cf:70:bc:4a (try 2/3)
[ 5857.516182] wlan0: direct probe to 00:02:cf:70:bc:4a (try 3/3)
[ 5857.716102] wlan0: direct probe to 00:02:cf:70:bc:4a timed out
[ 5865.820494] wlan0: direct probe to 00:02:cf:70:bc:4a (try 1/3)
[ 5866.020622] wlan0: direct probe to 00:02:cf:70:bc:4a (try 2/3)
[ 5866.220062] wlan0: direct probe to 00:02:cf:70:bc:4a (try 3/3)
[ 5866.420070] wlan0: direct probe to 00:02:cf:70:bc:4a timed out
[ 5874.496151] wlan0: direct probe to 00:02:cf:70:bc:4a (try 1/3)
[ 5874.696050] wlan0: direct probe to 00:02:cf:70:bc:4a (try 2/3)
[ 5874.896156] wlan0: direct probe to 00:02:cf:70:bc:4a (try 3/3)
[ 5875.096036] wlan0: direct probe to 00:02:cf:70:bc:4a timed out
[ 5883.224159] wlan0: direct probe to 00:02:cf:70:bc:4a (try 1/3)
[ 5883.424047] wlan0: direct probe to 00:02:cf:70:bc:4a (try 2/3)
[ 5883.624059] wlan0: direct probe to 00:02:cf:70:bc:4a (try 3/3)
[ 5883.824041] wlan0: direct probe to 00:02:cf:70:bc:4a timed out
[ 5891.928775] wlan0: direct probe to 00:02:cf:70:bc:4a (try 1/3)
[ 5892.128044] wlan0: direct probe to 00:02:cf:70:bc:4a (try 2/3)
[ 5892.328053] wlan0: direct probe to 00:02:cf:70:bc:4a (try 3/3)
[ 5892.528034] wlan0: direct probe to 00:02:cf:70:bc:4a timed out
[ 5900.611577] wlan0: direct probe to 00:02:cf:70:bc:4a (try 1/3)
[ 5900.808905] wlan0: direct probe to 00:02:cf:70:bc:4a (try 2/3)
[ 5901.008036] wlan0: direct probe to 00:02:cf:70:bc:4a (try 3/3)
[ 5901.208029] wlan0: direct probe to 00:02:cf:70:bc:4a timed out
[ 5909.334596] wlan0: direct probe to 00:02:cf:70:bc:4a (try 1/3)
[ 5909.532245] wlan0: direct probe to 00:02:cf:70:bc:4a (try 2/3)
[ 5909.732052] wlan0: direct probe to 00:02:cf:70:bc:4a (try 3/3)
[ 5909.932125] wlan0: direct probe to 00:02:cf:70:bc:4a timed out

```
**lshw -C network**
```
clement@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fb:b6:e0:d8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-26-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:48 memory:f8000000-f8001fff

```
**iwlist scan**
```
clement@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.

```
**build**
```
clement@ubuntu:~$ lsb_release -d
Description:	Ubuntu 12.04 LTS
clement@ubuntu:~$ uname -mr
3.2.0-26-generic x86_64

```
**rfkill list all**
```
clement@ubuntu:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
Note that all are ok now, but that is sometimes temperamental, but I can unblock them all by turning off/on wifi with hardware switch.

Am posting from this laptop right now, using an ethernet cable, which is working fine.  I also get the feeling that I may have caused some problems that may obscure the true issue, in my attempts to fix this myself.

Thanks for the help.

---

### Post by CDCM on 2012-07-29
When am I supposed to give up?

---

### Post by Department Q on 2012-09-26
The Intel 5100 is doomed.  It needs the iwlagn driver instead of the iwlwifi drier I think.  I am having a similar problem and I think the only one who knows how to fix this is Chili555.

I will post my issue here when I get the thread started.

---

