---
title: "Belkin Wireless G USB / rtl8187b not going faster than 11 M/sec"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by docbot on 2010-07-15
I have a little problem with my Belkin Wireless G Usb Stick (RTL8187b chip inside).

**The Problem** is that the Speed never exceeds 11 Mb/sec in the Connection Info when in theory it should be able to do 54 Mb/sec. The Driver also is listed as rtl8187 and not rtl8187b (which might not matter). I am new to Ubuntu and Linux.. so any help is appreciated!
I am using Ubuntu version 10.04 LTS if that matters.


**Already tried**

# logging into my thompson router and changing the channel form 6 to 7

# thompson router shows me connected as

xx:xx:xx:xx:xx:xx	0	-92	11g	192.168.0.11	userxy

since type is 11g and not 11b, it seems that I am connected under 802.11g

# I tried setting the speed manually via "sudo iwconfig wlan0 rate 54M", but if I set the value anything higher than 11M I cannot connect to the network.

# next I did "iwlist wlan0 scan" which said the following

Scan completed :
          Cell 01 - Address: xxxxxxxxxxxxxxxxxx
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"INTERNET FOREVER"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000380ec675
                    Extra: Last beacon: 23472ms ago
                    IE: Unknown: 0010494E5445524E455420464F5245564552
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

# than I tried "lsusb" to look at my USB settings

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 15d9:0a41 Dexon 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 012: ID 050d:705e Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

# than I tried "hwinfo"

70: None 00.0: 1070a WLAN
  [Created at net.124]
  Unique ID: AYEt.QXn1l67RSa1
  Parent ID: ADDn.7SML6AxhRm7
  SysFS ID: /class/net/wlan0
  SysFS Device Link: /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0
  Hardware Class: network interface
  Model: "WLAN network interface"
  Driver: "rtl8187"
  Driver Modules: "rtl8187"
  Device File: wlan0
  HW Address: 00:1c:df:47:42:91
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #61 (WLAN controller)


61: USB 00.0: 0282 WLAN controller
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_50d_705e_00e04c000001_if0
  Unique ID: ADDn.7SML6AxhRm7
  Parent ID: k4bc.9T1GDCLyFd9
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb1/1-1/1-1:1.0
  SysFS BusID: 1-1:1.0
  Hardware Class: network
  Model: "Belkin Wireless G USB Adapter"
  Hotplug: USB
  Vendor: usb 0x050d "Belkin Components"
  Device: usb 0x705e "Belkin Wireless G USB Adapter"
  Revision: "2.00"
  Serial ID: "00e04c000001"
  Driver: "rtl8187"
  Driver Modules: "rtl8187"
  Device File: wlan0
  Features: WLAN
  Speed: 480 Mbps
  HW Address: 00:1c:df:47:42:91
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 14
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472 2.484
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "usb:v050Dp705Ed0200dc00dsc00dp00icFFiscFFipFF"
  Driver Info #0:
    Driver Status: rtl8187 is active
    Driver Activation Cmd: "modprobe rtl8187"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #56 (Hub)

56: USB 00.0: 10a00 Hub
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1d_7_if0
  Unique ID: k4bc.9T1GDCLyFd9
  Parent ID: 5YuN.Lu7rTSAG4N5
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
  SysFS BusID: 1-0:1.0
  Hardware Class: hub
  Model: "Linux 2.6.32-23-generic ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 2.6.32-23-generic ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "2.06"
  Serial ID: "0000:00:1d.7"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #20 (USB Controller)


20: PCI 1d.7: 0c03 USB Controller (EHCI)
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_24dd
  Unique ID: 5YuN.Lu7rTSAG4N5
  SysFS ID: /devices/pci0000:00/0000:00:1d.7
  SysFS BusID: 0000:00:1d.7
  Hardware Class: usb controller
  Model: "Intel 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x24dd "82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x80a6 "P4P800/P5P800 series motherboard"
  Revision: 0x02
  Driver: "ehci_hcd"
  Driver Modules: "ehci_hcd"
  Memory Range: 0xf4fffc00-0xf4ffffff (rw,non-prefetchable)
  IRQ: 23 (11936636 events)
  Module Alias: "pci:v00008086d000024DDsv00001043sd000080A6bc0Csc03i20"
  Driver Info #0:
    Driver Status: ehci-hcd is not active
    Driver Activation Cmd: "modprobe ehci-hcd"
  Config Status: cfg=new, avail=yes, need=no, active=unknown


the only thing I noticed is that "ehci-hcd" is not active, which google tells me has something to do with usb 2.0 so maybe it's actually the usb ports faults that it won't go faster than 11 M? Modprobe ehci-hcd did not work though. everything worked fine under windows though.


Thanks alot!

---

### Post by docbot on 2010-07-18
bu bump

---

