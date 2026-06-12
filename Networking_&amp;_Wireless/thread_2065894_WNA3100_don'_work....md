---
title: "WNA3100 don' work..."
date: 2012-10-03
forum: Networking &amp; Wireless
---

### Post by isolachenonce on 2012-10-03
Hi guys... at first, sorry for my no good english, but i'll try to explain at well!! ;)

I've just installed Ubuntu 12.04 on my friend pc and i'm triyng to install the usb Netgear WNA3100 on pc... first time I tried to install the bcmwlhigh5 drivers, but they don't work... so I installed the bcmn43xx64 drivers, and now system see them but I can't connect the wi-fi...
These are my tests result...

```


angela@angela-desktop:~$ ndiswrapper -l

bcmn43xx64 : driver installed
   device (0846:9020) present


```

```


angela@angela-desktop:~$ sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 03
       serial: 00:25:22:5d:57:20
       size: 100Mbit/s


```

```


angela@angela-desktop:~$ lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 005: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 002: ID 03f0:b402 Hewlett-Packard PhotoSmart 7700 series
Bus 003 Device 002: ID 093a:2460 Pixart Imaging, Inc. Q-TEC WEBCAM 100
Bus 001 Device 006: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]


```

```


angela@angela-desktop:~$ dmesg | grep ndiswrapper

[   12.158792] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   12.908772] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   13.168254] usbcore: registered new interface driver ndiswrapper


```

Now, if I understand well, system see the usb device, the driver seems work fine and the network see wlan0 and read properly MAC router... in network manager is all ok and in connections list Netgear connection is ok... but when I try to connect, the usb device light go off and system ask me the connection password and don't connect!!! ](*,)

Can you help me?? Tnx!! :)

---

### Post by dark2099 on 2012-10-28
try doing
```
sudo depmod -a
sudo modprobe ndiswrapper
```

---

