---
title: "Cannot Get Verizon 4G VL600 Aircard to work"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by sfcg on 2011-02-10
Good afternoon. I've seen many posts on this so far. I actually postedone yesterday, but didn't get a response, so I figured I'd try a new one with more detail.

I have one of the new Verizon 4G VL600 usb aircards. I also have the UML290. I was able to get the UML290 working using wvdial, but I was not able to get the VL600 card working. I am trying to ditch windows, but unfortunately can't until I get this card working, because I had to give the working card to our support people.

This is a known issue, but I want to spur some more conversation regarding it.

Here are some of the diagnostics and output I have regarding the device:

-----------------------------------------------
/var/log/messages when the device is plugged in
-----------------------------------------------
Feb 10 14:47:13 ubuntu kernel: [17171.836489] usb 1-1.2: new high speed USB device using ehci_hcd and address 6
Feb 10 14:47:28 ubuntu kernel: [17187.543169] cdc_acm 1-1.2:1.2: ttyACM0: USB ACM device
Feb 10 14:47:28 ubuntu kernel: [17187.544127] usbcore: registered new interface driver cdc_acm
Feb 10 14:47:28 ubuntu kernel: [17187.544133] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
Feb 10 14:47:28 ubuntu kernel: [17187.565482] cdc_ether 1-1.2:1.0: eth1: register 'cdc_ether' at usb-0000:00:1a.0-1.2, CDC Ethernet Device, 64:99:5d:fc:96:f6
Feb 10 14:47:28 ubuntu kernel: [17187.565575] usbcore: registered new interface driver cdc_ether
----------------------------------------------------

So the device is showing up as what appears to be an ethernet adapter. In network manager it's showing up as a 'Wired' ethernet adapter.

Here is the output from lshw -c network and lsusb/lsusb -t

----------------------------------------------------

ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:06:f7:3a
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=0.12-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:f2500000-f251ffff memory:f2525000-f2525fff ioport:1820(size=32)
  *-network
       description: Wireless interface
       product: Centrino Advanced-N 6200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 35
       serial: 00:27:10:2c:4f:b8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-24-generic firmware=9.221.4.1 build 25532 ip=10.10.1.149 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:45 memory:f2400000-f2401fff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth1
       serial: 64:99:5d:fc:96:f6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device link=yes multicast=yes

ubuntu:~$ lsusb
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 1004:61aa LG Electronics, Inc. 
Bus 001 Device 005: ID 17ef:4816 Lenovo 
Bus 001 Device 004: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ubuntu:~$ lsusb -t
1-1.3:1.0: No such file or directory
1-1.4:1.2: No such file or directory
1-1.4:1.3: No such file or directory
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/8p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/6p, 480M
        |__ Port 2: Dev 6, If 0, Class=comm., Driver=cdc_ether, 480M
        |__ Port 2: Dev 6, If 1, Class=data, Driver=cdc_ether, 480M
        |__ Port 2: Dev 6, If 2, Class=comm., Driver=cdc_acm, 480M
        |__ Port 2: Dev 6, If 3, Class=data, Driver=cdc_acm, 480M
        |__ Port 3: Dev 3, If 0, Class=vend., Driver=, 12M
        |__ Port 4: Dev 4, If 0, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
        |__ Port 4: Dev 4, If 1, Class='bInterfaceClass 0xe0 not yet handled', Driver=btusb, 12M
        |__ Port 4: Dev 4, If 2, Class=vend., Driver=, 12M
        |__ Port 4: Dev 4, If 3, Class=app., Driver=, 12M
        |__ Port 6: Dev 5, If 0, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
        |__ Port 6: Dev 5, If 1, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
ubuntu:~$

-------------------------------------------------------

So all in all it looks like the device is showing up as an ethernet controller and the system itself is setting it up as eth1 in my case.

The throughput on this thing in covered areas is 18Mbps at times, which is friggin fast as far as I'm concerned. I would love to have that on the move, but I have no idea what to do from here.

What are your thoughts on this?

I'm using ubuntu 10.10 x32 dekstop, on a lenovo x201.

Thanks,

Chris

---

### Post by lisanels47 on 2011-02-11
I'm interested in this device also.  You say it shows up as a wired device?  After you plug it in and select the wired device, what happens?  What's in your /etc/resolv.conf file at that point, and what's the output of ifconfig?

---

### Post by balrog-kun on 2011-03-26
To update this thread, I posted the basic information on how to connect in the older related thread at [http://ubuntuforums.org/showpost.php?p=10604695&postcount=19](http://ubuntuforums.org/showpost.php?p=10604695&postcount=19)

---

