---
title: "Linksys WMP54G (rt61) in Jaunty"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by rkress on 2009-09-13
I can't get the above mentioned wireless card to detect any wireless networks. Here is as much information on it as I have. Machine is home built desktop. from the other threads I've seen this seems to be what working cards return (on the commands I've seen examples of). The windows drivers came from the linksys site that ndiswrapper is using.

lshw -c network:
```
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:04:06.0
       logical name: wlan0
       version: 00
       serial: 00:23:69:71:33:cb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt61 driverversion=1.53+Linksys, A Division of Cisc latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

iwconfig wlan0:
```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
lsmod | grep "ndiswrapper":
          ```
ndiswrapper           193436  0 
```


dmesg | grep -e ndis -e wlan:
```
[   10.694529] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   10.807029] ndiswrapper: driver rt61 (Linksys, A Division of Cisco Systems, Inc.,10/18/2005, 1.00.03.0000) loaded
[   10.807285] ndiswrapper 0000:04:06.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   10.822842] ndiswrapper: using IRQ 20
[   11.096738] wlan0: ethernet device 00:23:69:71:33:cb using serialized NDIS driver: rt61, version: 0x0, NDIS version: 0x500, vendor: 'Linksys Wireless-G PCI Adapter', 1814:0301.5.conf
[   11.096761] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   11.096844] usbcore: registered new interface driver ndiswrapper
[   13.400059] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.096202] ndiswrapper (mp_reset:64): wlan0 is being reset
[   73.096703] ndiswrapper (mp_reset:64): wlan0 is being reset
[  117.096332] ndiswrapper (mp_reset:64): wlan0 is being reset
[  161.096331] ndiswrapper (mp_reset:64): wlan0 is being reset
[  205.096573] ndiswrapper (mp_reset:64): wlan0 is being reset
[  249.096320] ndiswrapper (mp_reset:64): wlan0 is being reset
```

iwlist scan:
```
wlan0     No scan results
```

sudo etc/init.d/networking restart:
```
sudo: etc/init.d/networking: command not found
```

uname -mr:
```
2.6.28-15-generic i686
```

---

### Post by chili555 on 2009-09-14
Please try again:```
sudo [COLOR="Red"]/[/COLOR]etc/init.d/networking restart
[COLOR="Red"]sudo[/COLOR] iwlist wlan0 scan
```Also, could we please see:```
lsmod | grep rt
```Thanks.

---

### Post by Cuba71 on 2009-09-14
I believe RaLink provides a Linux driver for this device.

You need to obtain the Vendor ID and Product ID to find the right driver.

Then you can find the right info at [http://linux-wless.passys.nl/query_alles.php]("http://linux-wless.passys.nl/query_alles.php")

---

