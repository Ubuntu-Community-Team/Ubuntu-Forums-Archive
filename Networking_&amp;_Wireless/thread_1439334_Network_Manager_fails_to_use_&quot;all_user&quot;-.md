---
title: "Network Manager fails to use &quot;all user&quot;-stored wireless passwords"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by airbaggins on 2010-03-26
Hi.

I occasionally have a bad connection to my wireless router, but it generally works ok. When I get connection drops of the wireless, ubuntu often struggles to remember the password. I have gone into the nm-connection-editor and set up the MAC address for our single access point, set the encryption password and set it to connect automatically, but often, it just decides it doesn't want to use it again after the first time and asks me to re-enter the wireless password and it creates a new config. So I end up with several "Auto myssidhere" connection configs and have to enter my password every single time i get disconnected, which is getting a little bit old now.

I would like network manager to just persist and keep trying to connect to the network configs I already have for a given SSID, without me having to create a new configuration every time I have flakey reception. Also, if I get completely disconnected, and I select the SSID from the drop down on the nm-applet, it will create a new configuration.

Does anyone have any ideas? This seems like a bug in the network-manager to me.

Any more info gladly provided, any help or ideas gladly recieved. :)

Thanks
-Bill


lsusb says this about my adapter (branded Edimax, which I bought specifically from a linux-specialised hardware vendor):
```
Bus 001 Device 004: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
```

dmesg says this when I connect it :
```
[ 1587.240018] usb 1-1: new high speed USB device using ehci_hcd and address 4
[ 1587.523288] usb 1-1: configuration #1 chosen from 1 choice
[ 1587.633094] phy4 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[ 1587.633100] phy4 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[ 1587.896478] phy5: Selected rate control algorithm 'minstrel'
[ 1587.897100] Registered led device: rt73usb-phy5::radio
[ 1587.897116] Registered led device: rt73usb-phy5::assoc
[ 1587.897131] Registered led device: rt73usb-phy5::quality
[ 1587.907727] rt73usb 1-1:1.0: firmware: requesting rt73.bin
[ 1588.035208] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1674.151010] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

uname -a
```
Linux bill-desktop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux
```

lsb_release -a
```
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic
```

---

