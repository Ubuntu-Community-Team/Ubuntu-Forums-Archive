---
title: "New kernel 2.6.32.3 and no wireless networking"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by bubblechaser on 2010-01-16
Im on 9.04 and i upgraded to the latest kernel. Pretty much a default .config for a kernel few things here and there removed. When i boot into the kernel and go to connect to the wifi it shows enable wireless grayed out and enable networking checked.

```
alert@alert-desktop:~$ lshw -c net
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82547EI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth1
       version: 00
       serial: 00:e0:81:2b:78:ea
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A latency=0 mingnt=255 module=e1000 multicast=yes
  *-network:0
       description: Ethernet interface
       product: 82541GI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       logical name: eth2
       version: 00
       serial: 00:e0:81:2b:78:eb
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A latency=32 mingnt=255 module=e1000 multicast=yes
  *-network:1
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:03:06.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:2
       description: Ethernet interface
       product: 82801EB/ER (ICH5/ICH5R) integrated LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 02
       serial: 00:e0:81:2b:78:ec
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:06:25:1b:4a:35
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.121 multicast=yes wireless=IEEE 802.11b
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:2 DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: pan0
       serial: 16:69:d2:74:29:57
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

dmesg
```
[   28.449987] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.469070] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   28.470929] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   28.504052] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
[   28.584573] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[   28.625948] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[   28.776055] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   28.836062] b43legacy-phy0 debug: Chip initialized
[   28.836325] b43legacy-phy0 debug: 30-bit DMA initialized
[   28.836467] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x2B
[   28.836474] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x78
[   28.836480] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x2E
[   28.836488] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x19
[   28.836526] b43legacy-phy0 debug: Wireless interface started
[   28.836573] b43legacy-phy0: Radio hardware status changed to DISABLED
[   28.836583] b43legacy-phy0 debug: Radio initialized
[   28.837433] b43legacy-phy0 debug: Adding Interface type 2
[   28.892070] b43legacy-phy0: Radio turned on by software
[   28.892078] b43legacy-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[   28.892375] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   28.932079] b43legacy-phy0 debug: Removing Interface type 2
[   28.940077] b43legacy-phy0 debug: Wireless interface stopped

[  550.833436] phy1: Selected rate control algorithm 'minstrel'
[  550.835376] phy1: hwaddr 00:c0:ca:20:16:c4, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[  550.846653] rtl8187: Customer ID is 0xFF
[  550.847035] Registered led device: rtl8187-phy1::tx
[  550.847689] Registered led device: rtl8187-phy1::rx
[  550.850705] rtl8187: wireless switch is on
[  550.850816] usbcore: registered new interface driver rtl8187
[  557.405099] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

it can scan the network
```
alert@alert-desktop:~$ sudo !!
sudo iwlist wlan0 scan
[sudo] password for alert: 
wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:06:F0:23
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"jalapeno & cheddar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002be8d1d6359
                    Extra: Last beacon: 888ms ago
                    IE: Unknown: 00126A616C6170656E6F20262063686564646172
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000052435E0062322F00
```


digging through the logs and it points me to a firefox bug??
NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))

---

### Post by bkratz on 2010-01-16
[   28.837433] b43legacy-phy0 debug: Adding Interface type 2
[   28.892070] b43legacy-phy0: Radio turned on by software
[   28.892078] b43legacy-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[   28.892375] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   28.932079] b43legacy-phy0 debug: Removing Interface type 2
[   28.940077] b43legacy-phy0 debug: Wireless interface stopped


Well it does say that the switch is turned off (pushbutton)
In this line

[   28.892078] b43legacy-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.


Hope it helps

---

