---
title: "Bluetooth Internet Connection"
date: 2006-04-13
forum: Networking &amp; Wireless
---

### Post by hussain387 on 2006-04-13
hi fellow,s
 i am newbie i have just installed breezie ok my quetion is how can i share internet connection with bluetooth  i get internet through cable which is eth1 on my breeze.
i can send and recieve  files through bluetooth dongle  now i need to share iternet connection through breeze to my xp plzzzz help
lshw -C network
 WARNING: you should run this program as super-user.
  *-usb
       description: Bluetooth wireless interface
       product: Bluetooth Dongle (HCI mode)
       vendor: Cambridge Silicon Radio, Ltd
       physical id: 2
       bus info: usb@1:2
       version: 5.25
       capabilities: bluetooth usb-1.10
       configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       product: 82557/8/9 [Ethernet Pro 100]
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth0
       version: 05
       serial: 00:50:8b:0d:28:45
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 multicast=yes
       resources: iomemory:f8000000-f8000fff ioport:bc00-bc1f iomemory:ff700000-ff7fffff irq:17
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth1
       version: 01
       serial: 00:11:11:57:da:fa
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 ip=10.0.0.34 multicast=yes
       resources: iomemory:ff900000-ff900fff ioport:b800-b83f irq:20

---

