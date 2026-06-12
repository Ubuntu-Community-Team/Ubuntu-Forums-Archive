---
title: "Logitech WiLife home security cameras"
date: 2012-10-19
forum: Networking &amp; Wireless
---

### Post by Doles284 on 2012-10-19
I've recently acquired some Logitech Network security cameras

I want to use them with Motion on Ubuntu 10.04

Anyway, I'm just having trouble working out how to access the cameras. I've just plugged one in so far and here's what is happening:

it shows up in lsusb
```
Bus 002 Device 003: ID 09e1:5121 Intellon Corp. MicroLink dLAN

```


here is what happens in dmesg
```
[42733.391780] hub 1-4.1:1.0: connect-debounce failed, port 2 disabled
[42745.490100] hub 2-0:1.0: unable to enumerate USB device on port 1
[42745.830057] usb 2-1: new full speed USB device using ohci_hcd and address 3
[42746.068797] usb 2-1: configuration #1 chosen from 1 choice
[42746.071793] usb 2-1: bad CDC descriptors
[42746.083277] eth2: register 'int51x1' at usb-0000:00:04.0-1, Intellon usb powerline adapter, 00:12:ab:05:d5:e4
[42746.116308] udev: renamed network interface eth2 to eth4
[42756.560023] eth4: no IPv6 routers present
```

ifconfig
```
eth4      Link encap:Ethernet  HWaddr 00:12:ab:05:d5:e4  
          inet6 addr: fe80::212:abff:fe05:d5e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4253 (4.2 KB)  TX bytes:2330 (2.3 KB)
```

How do I make use of this information? The camera/device has an IPv6 address, but I don't know how to view it or tell motion where it lives. Let alone if it's even working at all

---

