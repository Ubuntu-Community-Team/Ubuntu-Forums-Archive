---
title: "Intel Centrino Advanced-N 6205 not working on XUbuntu 11.4"
date: 2012-07-06
forum: Networking &amp; Wireless
---

### Post by duksdalben on 2012-07-06
Hey,

I just can't connect to a wirless Network using the build in networkdevice. The Networkmanger shows "device not manged". It has been connected to the network during the setup prozess. 

Another usb Wirlesscard is working perfect (curently pluged in under wlan1) but I want to use the buildin.

Here are some Information's. If you need more just ask.

[B]
1 ) Machine Brand and Model (PC/Laptop)[/B]:
Laptop Thinkpad x220

**2 ) Wireless Brand, Model and Wireless Chip****set:**
     ```
$ lspci -nn | grep -i Net 
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0085] (rev 34)
```
Intel Centrino Advanced-N 6205

[B]3 ) check interface:
[/B]     
     ```
$ ifconfig wlan0     Link encap:Ethernet  HWaddr a0:88:b4:40:ec:bc  
          inet addr:192.168.178.15  Bcast:192.168.178.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  $ iwconfig 
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```[B]4 ) Check for modules:
[/B]     ```
$ lsmod | grep iwlagn 
 returns nothing.

```[B]5 ) Kernel boot messages
[/B]     
     ```
$ dmesg | grep -i iwl
[   63.116358] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   63.116397] iwlwifi 0000:03:00.0: setting latency timer to 64
[   63.116438] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   63.116439] iwlwifi 0000:03:00.0: pci_resource_base = ffffc900057f8000
[   63.116440] iwlwifi 0000:03:00.0: HW Revision ID = 0x34
[   63.116768] iwlwifi 0000:03:00.0: irq 47 for MSI/MSI-X
[   63.116853] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   63.116854] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   63.116856] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   63.116857] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE disabled
[   63.116858] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[   63.116886] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[   63.116963] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   63.127561] iwlwifi 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[   63.127563] iwlwifi 0000:03:00.0: Device SKU: 0x1F0
[   63.127564] iwlwifi 0000:03:00.0: Valid Tx ant: 0x3, Valid Rx ant: 0x3
[   63.127575] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   63.177148] iwlwifi 0000:03:00.0: loaded firmware version 17.168.5.3 build 42301
[   63.415986] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   63.431936] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   63.432143] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   63.719672] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   63.719871] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[  202.407636] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[  202.451931] iwlwifi 0000:03:00.0: Command REPLY_RXON aborted: RF KILL Switch
[  202.451969] iwlwifi 0000:03:00.0: Not sending command - RF KILL
[  205.596320] iwlwifi 0000:03:00.0: RF_KILL bit toggled to enable radio.
[ 1193.750655] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[ 1193.750851] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0

```
[B]6 ) Network configuration
[/B]     ```
Code:
     $ lshw -C network 
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6205
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: a0:88:b4:40:ec:bc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-26-generic firmware=17.168.5.3 build 42301 ip=192.168.178.15 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:f2400000-f2401fff
```
[B]7 ) Scan for networks:
[/B]     Code:
     ```
$ iwlist scan

 wlan0     No scan results

```[B]8 ) Ubuntu Version: 
[/B]     Code:
     ```
$ lsb_release -d 
Description:    Ubuntu 12.04 LTS 
```[B]9 ) Kernel/architecture (including 32 vs. 64 bit): 
[/B]     Code:
     ```
$ uname -mr

3.2.0-26-generic x86_64

```Thanks in advance for your help!

---

### Post by chili555 on 2012-07-06
Please detach the USB wireless, make sure the wireless switch is set to ON and run and post:```
rfkill list all
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```Thanks.

It is very confusing to try to sort the readings between built-in and USB, so when we are running diagnostics, please be sure the USB is detached.

---

### Post by duksdalben on 2012-07-06
Ok, i'll remove the externel one. But I need to replug it to post the results.

```
$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````
$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

```I've just removed the configuration of the wlan0 out of this file. It doesn't make sense there, if I want to mange this with the Networkmanger. Thanks for the hint.


```
$ cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]managed=false

```Now the Networkmanger print: "Device not ready".

---

### Post by chili555 on 2012-07-06
So far, so good! Now, again with the USB detached, please let me see:```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by duksdalben on 2012-07-07
The rusult:

```
$ sudo iwlist wlan0 scan

wlan0     Interface doesn't support scanning : Network is down
```

Edit: rebooting solved this error.  @chili555: Thank's for your help and time. :)

---

