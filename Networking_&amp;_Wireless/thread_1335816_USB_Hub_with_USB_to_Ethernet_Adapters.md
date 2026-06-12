---
title: "USB Hub with USB to Ethernet Adapters"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by stormproof on 2009-11-23
output of dmesg after connecting the USB HUB - LOOKS GOOD

usb 1-4: new high speed USB device using ehci_hcd and address 29
usb 1-4: configuration #1 chosen from 1 choice
hub 1-4:1.0: USB hub found
hub 1-4:1.0: 7 ports detected
usb 1-4: New USB device found, idVendor=1a40, idProduct=0201
usb 1-4: New USB device strings: Mfr=0, Product=1, SerialNumber=0
usb 1-4: Product: USB 2.0 Hub [MTT]



tail -f /var/log/messages - LOOKS GOOD

Nov 23 20:22:47 linux-tf9s kernel: usb 1-4: new high speed USB device using ehci_hcd and address 29
Nov 23 20:22:47 linux-tf9s kernel: usb 1-4: configuration #1 chosen from 1 choice
Nov 23 20:22:47 linux-tf9s kernel: hub 1-4:1.0: USB hub found
Nov 23 20:22:47 linux-tf9s kernel: hub 1-4:1.0: 7 ports detected
Nov 23 20:22:47 linux-tf9s kernel: usb 1-4: New USB device found, idVendor=1a40, idProduct=0201
Nov 23 20:22:47 linux-tf9s kernel: usb 1-4: New USB device strings: Mfr=0, Product=1, SerialNumber=0
Nov 23 20:22:47 linux-tf9s kernel: usb 1-4: Product: USB 2.0 Hub [MTT]



output from the /var/log/messages after I connect the usb to ethernet adapter to the usb hub - LOOKS GOOD

Nov 23 20:24:34 linux-tf9s kernel: usb 1-4.1: new full speed USB device using ehci_hcd and address 30
Nov 23 20:24:34 linux-tf9s kernel: usb 1-4.1: configuration #1 chosen from 1 choice
Nov 23 20:24:34 linux-tf9s kernel: usb 1-4.1: New USB device found, idVendor=0fe6, idProduct=8101
Nov 23 20:24:34 linux-tf9s kernel: usb 1-4.1: New USB device strings: Mfr=0, Product=2, SerialNumber=3
Nov 23 20:24:34 linux-tf9s kernel: usb 1-4.1: Product: USB Network Controller
Nov 23 20:24:34 linux-tf9s kernel: usb 1-4.1: SerialNumber:


after I connect another usb to ethernet adapter to usb hub - LOOKS GOOD

Nov 23 20:24:34 linux-tf9s kernel: usb 1-4.1: new full speed USB device using ehci_hcd and address 30
Nov 23 20:24:34 linux-tf9s kernel: usb 1-4.1: configuration #1 chosen from 1 choice
Nov 23 20:24:34 linux-tf9s kernel: usb 1-4.1: New USB device found, idVendor=0fe6, idProduct=8101
Nov 23 20:24:34 linux-tf9s kernel: usb 1-4.1: New USB device strings: Mfr=0, Product=2, SerialNumber=3
Nov 23 20:24:34 linux-tf9s kernel: usb 1-4.1: Product: USB Network Controller
Nov 23 20:24:34 linux-tf9s kernel: usb 1-4.1: SerialNumber:
Nov 23 20:26:19 linux-tf9s kernel: usb 1-4.2: new full speed USB device using ehci_hcd and address 31
Nov 23 20:26:19 linux-tf9s kernel: usb 1-4.2: configuration #1 chosen from 1 choice
Nov 23 20:26:19 linux-tf9s kernel: usb 1-4.2: New USB device found, idVendor=0fe6, idProduct=8101
Nov 23 20:26:19 linux-tf9s kernel: usb 1-4.2: New USB device strings: Mfr=0, Product=2, SerialNumber=3
Nov 23 20:26:19 linux-tf9s kernel: usb 1-4.2: Product: USB Network Controller
Nov 23 20:26:19 linux-tf9s kernel: usb 1-4.2: SerialNumber:

and another usb to ethernet adapter gets plugged into the hub - LOOKS GOOD


Nov 23 20:24:34 linux-tf9s kernel: usb 1-4.1: new full speed USB device using ehci_hcd and address 30
Nov 23 20:24:34 linux-tf9s kernel: usb 1-4.1: configuration #1 chosen from 1 choice
Nov 23 20:24:34 linux-tf9s kernel: usb 1-4.1: New USB device found, idVendor=0fe6, idProduct=8101
Nov 23 20:24:34 linux-tf9s kernel: usb 1-4.1: New USB device strings: Mfr=0, Product=2, SerialNumber=3
Nov 23 20:24:34 linux-tf9s kernel: usb 1-4.1: Product: USB Network Controller
Nov 23 20:24:34 linux-tf9s kernel: usb 1-4.1: SerialNumber:
Nov 23 20:26:19 linux-tf9s kernel: usb 1-4.2: new full speed USB device using ehci_hcd and address 31
Nov 23 20:26:19 linux-tf9s kernel: usb 1-4.2: configuration #1 chosen from 1 choice
Nov 23 20:26:19 linux-tf9s kernel: usb 1-4.2: New USB device found, idVendor=0fe6, idProduct=8101
Nov 23 20:26:19 linux-tf9s kernel: usb 1-4.2: New USB device strings: Mfr=0, Product=2, SerialNumber=3
Nov 23 20:26:19 linux-tf9s kernel: usb 1-4.2: Product: USB Network Controller
Nov 23 20:26:19 linux-tf9s kernel: usb 1-4.2: SerialNumber:
Nov 23 20:27:16 linux-tf9s kernel: usb 1-4.3: new full speed USB device using ehci_hcd and address 32
Nov 23 20:27:16 linux-tf9s kernel: usb 1-4.3: configuration #1 chosen from 1 choice
Nov 23 20:27:16 linux-tf9s kernel: usb 1-4.3: New USB device found, idVendor=0fe6, idProduct=8101
Nov 23 20:27:16 linux-tf9s kernel: usb 1-4.3: New USB device strings: Mfr=0, Product=2, SerialNumber=3
Nov 23 20:27:16 linux-tf9s kernel: usb 1-4.3: Product: USB Network Controller
Nov 23 20:27:16 linux-tf9s kernel: usb 1-4.3: SerialNumber:


OK I think you get the picture now, everything appears to look good from the output. Here is the output of

lsusb


linux-tf9s:/proc # lsusb - LOOKS GOOD
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 046e:5542 Behavior Tech. Computer Corp.
Bus 002 Device 003: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 032: ID 0fe6:8101 
Bus 001 Device 031: ID 0fe6:8101 
Bus 001 Device 030: ID 0fe6:8101 
Bus 001 Device 029: ID 1a40:0201 TERMINUS TECHNOLOGY INC.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



Finally here is the output of ifconfig -a

linux-tf9s:/proc # ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:A0:C9:E0:FD:ED 
          inet6 addr: fe80::2a0:c9ff:fee0:fded/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2520 (2.4 Kb)

eth1      Link encap:Ethernet  HWaddr 00:0D:61:25:D4:6A 
          inet6 addr: fe80::20d:61ff:fe25:d46a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2178 (2.1 Kb)
          Interrupt:16 Base address:0x6000

eth2      Link encap:Ethernet  HWaddr 00:40:F4:5F:F5:53 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xa000

eth3      Link encap:Ethernet  HWaddr 00:48:54:87:68:38 
          inet6 addr: fe80::248:54ff:fe87:6838/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:2520 (2.4 Kb)
          Interrupt:18 Base address:0xa000

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:440 (440.0 b)  TX bytes:440 (440.0 b)


BLUETOOTH INTERFACE


pan0      Link encap:Ethernet  HWaddr A6:54:32:0E:37:61 
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



THESE TWO INTERFACES ARE FOR MY WIRELESS NIC IN MY LINUX BOX


wlan0     Link encap:Ethernet  HWaddr 00:1E:E5:FB:E5:30 
          inet addr:172.16.2.5  Bcast:172.16.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:e5ff:fefb:e530/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3971991 (3.7 Mb)  TX bytes:986163 (963.0 Kb)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-E5-FB-E5-30-35-33-00-00-00-00-00-00-00-00 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



As you can see there are no usb1 or usb2 or 3 interfaces. Can you shed some light on this. Any help would be greatly appreciated.

I found this link that has some good info but I still have the problem
[http://www.linux-usb.org/usbnet/#t-enet](http://www.linux-usb.org/usbnet/#t-enet)

---

