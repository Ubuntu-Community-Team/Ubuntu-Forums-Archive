---
title: "Wireless connection stops working randomly"
date: 2011-08-23
forum: Networking &amp; Wireless
---

### Post by raja.iyer on 2011-08-23
Hi 
I have a problem with my wireless connection in ubuntu (natty  with amd64bit) . There seems to be intermittent disruption in my connection. Havent seen a pattern as yet, though it happens once a day. After that I cant get it to work at all and only restarting + reconnecting the USB device helps. Dont know what is going on. 

I have already read these pages :[ Commands]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Commands") and [Wireless Troubleshooting]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide").

Here is my line of though
1) Given that I am able to connect other devices to it while I am not able to connect through this desktop, I think the router is OK. 
2) I am able to work with it after restart + re-connection . And so the driver is OK and is loaded. The driver seems to be oK and loaded even while I am not able to connect. 

So why is this happening and how can I get this under control without having to reboot and re-connect the device everytime. 
Can I try something that I have not yet tried ? Any suggestion is welcome.

Here are the output for the commands which will give you a more detailed idea of the process. 

Before reboot while I was not able to connect:
```
Script started on Tue 23 Aug 2011 01:40:08 PM CDT
raja@UshRaj: ~raja@UshRaj:~$ sudo nm-tool 
[sudo] password for raja: 

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            ATL1E
  State:             unavailable
  Default:           no
  HW Address:        XX:XX:XX:XX:XX:XX

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ar9170usb
  State:             disconnected
  Default:           no
  HW Address:        XX:XX:XX:XX:XX:XX

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


raja@UshRaj: ~raja@UshRaj:~$ sudo lshw -C network
DMI   SMP   PA-RISC       device-tree           SPD   memory      /proc/cpuinfo             CPUID     PCI (sysfs)           ISA PnP       PCMCIA      PCMCIA      kernel device tree (sysfs)                          USB   IDE   SCSI    Network interfaces                  Framebuffer devices                   Display       CPUFreq       ABI     *-network
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: XX:XX:XX:XX:XX:XX
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:fbec0000-fbefffff ioport:dc00(size=128)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan0
       serial: XX:XX:XX:XX:XX:XX
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ar9170usb driverversion=2.6.38-10-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn
raja@UshRaj: ~raja@UshRaj:~$ sudo lsusb 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c03f Logitech, Inc. UltraX Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 0846:9001 NetGear, Inc. WN111(v2) RangeMax Next Wireless [Atheros AR9001U-(2)NG]
Bus 001 Device 004: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
raja@UshRaj: ~raja@UshRaj:~$ sudo lsusb -v -s 001:007

Bus 001 Device 007: ID 0846:9001 NetGear, Inc. WN111(v2) RangeMax Next Wireless [Atheros AR9001U-(2)NG]
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x0846 NetGear, Inc.
  idProduct          0x9001 WN111(v2) RangeMax Next Wireless [Atheros AR9001U-(2)NG]
  bcdDevice            1.06
  iManufacturer          16 ATHER
  iProduct               32 USB2.0 WLAN
  iSerial                48 12345
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)
raja@UshRaj: ~raja@UshRaj:~$ sudo lsmod | grep 9170
carl[01;31m[K9170[m[K               82764  0 
ar[01;31m[K9170[m[Kusb              54760  0 
mac80211              294370  2 carl[01;31m[K9170[m[K,ar[01;31m[K9170[m[Kusb
ath                    23773  2 carl[01;31m[K9170[m[K,ar[01;31m[K9170[m[Kusb
cfg80211              178528  4 carl[01;31m[K9170[m[K,ar[01;31m[K9170[m[Kusb,mac80211,ath
raja@UshRaj: ~raja@UshRaj:~$ sudo modprobe -r at9170usb
raja@UshRaj: ~raja@UshRaj:~$ sudo modprobe ar9170usb
raja@UshRaj: ~raja@UshRaj:~$ sudo iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
raja@UshRaj: ~raja@UshRaj:~$ sudo iwconfig wlan0 scan
wlan0     No scan results

raja@UshRaj: ~raja@UshRaj:~$ sudo iwconfig wlan0 essid "Ubujuju"
[sudo] password for raja: 
raja@UshRaj: ~raja@UshRaj:~$ sudo iwconfig wlan0 key XXXX-XXXX-XX
raja@UshRaj: ~raja@UshRaj:~$ sudo iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Ubujuju"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:XXXX-XXXX-XX
          Power Management:off
          
raja@UshRaj: ~raja@UshRaj:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

raja@UshRaj: ~raja@UshRaj:~$ exit

Script done on Tue 23 Aug 2011 03:17:56 P
```

After reboot while I was able to connect:

```
Script started on Tue 23 Aug 2011 03:37:06 PM CDT
raja@UshRaj: $ sudo iwconfig 
[sudo] password for raja: 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Ubujuju"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:XXXX-XXXX-XX
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:98   Missed beacon:0

raja@UshRaj: $ sudo nm-tool 

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            ATL1E
  State:             unavailable
  Default:           no
  HW Address:        XX:XX:XX:XX:XX:XX

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Wireless connection 1] ---------------------------------------
  Type:              802.11 WiFi
  Driver:            ar9170usb
  State:             connected
  Default:           yes
  HW Address:        XX:XX:XX:XX:XX:XX

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Ubujuju:        Infra, XX:XX:XX:XX:XX:XX, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WEP

  IPv4 Settings:
    Address:         192.168.1.144
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


raja@UshRaj:~$ lshw -C network
DMI   SMP   PA-RISC       device-tree           SPD   memory      /proc/cpuinfo             CPUID     PCI (sysfs)           ISA PnP       PCMCIA      PCMCIA      kernel device tree (sysfs)                          USB   IDE   SCSI    Network interfaces                  Framebuffer devices                   Display       CPUFreq       ABI     *-network
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: XX:XX:XX:XX:XX:XX
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:fbec0000-fbefffff ioport:dc00(size=128)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan0
       serial: XX:XX:XX:XX:XX:XX
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ar9170usb driverversion=2.6.38-11-generic firmware=N/A ip=192.168.1.144 link=yes multicast=yes wireless=IEEE 802.11bgn
raja@UshRaj: $ lsmod | grep 9170
carl[01;31m[K9170[m[K               82764  0 
ar[01;31m[K9170[m[Kusb              54760  0 
mac80211              294370  2 carl[01;31m[K9170[m[K,ar[01;31m[K9170[m[Kusb
ath                    23773  2 carl[01;31m[K9170[m[K,ar[01;31m[K9170[m[Kusb
cfg80211              178528  4 carl[01;31m[K9170[m[K,ar[01;31m[K9170[m[Kusb,mac80211,ath
raja@UshRaj: $ lsmod | grep 9170usb 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c03f Logitech, Inc. UltraX Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0846:9001 NetGear, Inc. WN111(v2) RangeMax Next Wireless [Atheros AR9001U-(2)NG]
Bus 001 Device 002: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
raja@UshRaj: $ sudo lsusb -v -s 001:005 

Bus 001 Device 005: ID 0846:9001 NetGear, Inc. WN111(v2) RangeMax Next Wireless [Atheros AR9001U-(2)NG]
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  idVendor           0x0846 NetGear, Inc.
  idProduct          0x9001 WN111(v2) RangeMax Next Wireless [Atheros AR9001U-(2)NG]
  bcdDevice            1.06
  iManufacturer          16 ATHER
  iProduct               32 USB2.0 WLAN
  iSerial                48 12345
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass       255 Vendor Specific Subclass
  bDeviceProtocol       255 Vendor Specific Protocol
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)
raja@UshRaj: $ cat /etc/network/interfaces
auto lo
iface lo inet loopback

raja@UshRaj: $ exit

Script done on Tue 23 Aug 2011 03:41:45 PDT
```

Thanks
Raja

---

### Post by praseodym on 2011-08-23
Hello,

check with

```
lsmod | grep 9170
```

if two modules (ar9170usb and carl9170) are loaded. If so, blacklist the older one:

```
echo "blacklist ar9170usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot. Check:

```
lsmod | grep 9170
dmesg | grep 9170
iwconfig
```

---

### Post by raja.iyer on 2011-08-23
Dear praseodym

Thank you for your response. I did wonder about it but wasn't sure of what it meant to have 2 modules there. Anyways, I have taken the necessary step. I hope things go smoothly. 

```

raja@UshRaj:~$ lsmod | grep 9170
carl9170               82764  0 
mac80211              294370  1 carl9170
ath                    23773  1 carl9170
cfg80211              178528  3 carl9170,mac80211,ath
raja@UshRaj:~$ dmesg | grep 9170
[   17.889484] usbcore: registered new interface driver carl9170
[   18.517940] Registered led device: carl9170-phy0::tx
[   18.517943] usb 1-4: Atheros AR9170 is registered as 'phy0'
[   18.519170] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
raja@UshRaj:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Ubujuju"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: XX:xx:xx:xx:xx:xx   
          Bit Rate=54 Mb/s Tx-Power=27 dBm   
          Retry  long limit:7 RTS thr:off Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:31 Missed beacon:0

```

Thanks
Raja

---

### Post by praseodym on 2011-08-24
Does it work? Check the messages if errors occur:

```
dmesg | egrep '9170|firm|wlan0'
```

---

