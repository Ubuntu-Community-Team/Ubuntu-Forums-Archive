---
title: "zd1211-base WIFI USB key with extension cable works ONLY during installation Oneiric"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by vratojr on 2011-10-23
Hello, I have a USB WIFI key plugged to a 3m USB cable extension. The key worked perfectly during the installation of Ubuntu 11.10 64bit but, after reboot it stops working.

lsusb
```
Bus 001 Device 006: ID 1435:0711 Wistron NeWeb UR055G 802.11bg
```This is the output I get:

dmesg:
```
[62973.868040] usb 1-6: new high speed USB device number 8 using ehci_hcd
[62974.116042] usb 1-6: reset high speed USB device number 8 using ehci_hcd
...
[62974.250024] ieee80211 phy3: Selected rate control algorithm 'minstrel_ht'
[62974.251186] zd1211rw 1-6:1.0: phy3
[62974.356966] usb 1-6: USB control request for firmware upload failed. Error number -71
[62974.356979] usb 1-6: Could not upload firmware code uph. Error number -71
```But the error code shifts from 71 to 110 to 29

lshw -C network:
```
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:6
       logical name: wlan0
       serial: 00:10:a7:2e:ce:e9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

```
While this is the output I get if I use the key without the extension cable (and works perfectly):

dmesg
```
[62812.848038] usb 1-10: reset high speed USB device number 7 using ehci_hcd
....
[62812.982194] ieee80211 phy2: Selected rate control algorithm 'minstrel_ht'
[62812.983523] zd1211rw 1-10:1.0: phy2
[62813.127055] zd1211rw 1-10:1.0: firmware version 4605
[62813.167054] zd1211rw 1-10:1.0: zd1211 chip 1435:0711 v4330 high 00-10-a7 AL2230_RF pa0 g----

```lshw -C network:
```
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:10
       logical name: wlan0
       serial: 00:10:a7:2e:ce:e9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw driverversion=3.0.0-12-generic firmware=4605 ip=5.236.27.75 link=yes multicast=yes wireless=IEEE 802.11bg

```

Can anyone help me, please?

Thanks!

---

