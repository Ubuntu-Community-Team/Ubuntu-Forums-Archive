---
title: "ZD1211 no longer working - Shuttle PN18 / 8.10"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by alkaboy on 2009-01-31
My USB wireless card, a Shuttle PN18 based on the zd1211 chipset, is all of a sudden no longer working properly. I used to be able to browse wireless networks in my building and now can no longer see any networks or connect to mine.

I'm using network-manager / nm-applet and would love to be able to keep using the graphical interface to connect. Help please!


Here is some relevant info:
Computer: Shuttle SB95P v2
Kernel: 2.6.27-11-generic i686

lspci: nothing mentioned
lsusb: nothing mentioned

ifconfig (eth0 is my ethernet, not wireless):
```
eth0      Link encap:Ethernet  HWaddr 00:30:1b:b9:cb:f1  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18812 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19679 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16954322 (16.9 MB)  TX bytes:3565070 (3.5 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)
```

iwconfig:
```
...
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
...
```

lsmod:
```
...
mac80211              216820  1 zd1211rw
...
usbcore               149360  7 zd1211rw,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
...
```

lshw:
```
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:12:0e:08:19:ad
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

iwlist scan:
```
...
wlan0     No scan results
...
```

dmesg:
```
...
[   34.648467] firmware: requesting zd1211/zd1211_ub
[   34.651837] firmware: requesting zd1211/zd1211_uphr
[   34.665113] usb 5-5.1: USB control request for firmware upload failed. Error number -32
[   34.665122] usb 5-5.1: Could not upload firmware code uph. Error number -32
[   34.665150] zd1211rw 5-5.1:1.0: couldn't load firmware. Error number -32
...
```

---

