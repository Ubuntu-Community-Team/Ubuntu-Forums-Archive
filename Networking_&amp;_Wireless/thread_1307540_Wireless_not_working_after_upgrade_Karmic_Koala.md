---
title: "Wireless not working after upgrade Karmic Koala"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by amacus on 2009-10-31
Hi everybody,

I have just upgraded to Karmic Koala 64-bit, and the previously (9.04) working wireless is now not! Network-manager can see a wireless network, and asks for authentication, but then the blue circle just keeps spinning and eventually it will ask me for authentication again but not connect. I have seen posts about this for Broadcom drivers, but not for my Tenda Wireless N adaptor (with Ralink chipset)

I have tried:
Installing wicd. Wicd could see the network too, but when it tried to connect would fail with the error "Could not obtain IP address"
Disabling WEP on my router - still could not connect

```

lsusb -v
``````
Bus 001 Device 003: ID 148f:2870 Ralink Technology, Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x148f Ralink Technology, Corp.
  idProduct          0x2870 
  bcdDevice            1.01
  iManufacturer           1 Ralink
  iProduct                2 802.11 n WLAN
  iSerial                 3 1.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           53
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              450mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           5
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 1.0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
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
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

``````
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"O2wireless770221"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=7 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```dmesg

```
[   23.861255] eth0: no IPv6 routers present
[   51.279774] wlan0: authenticate with AP 00:24:17:31:cc:b3
[   51.281780] wlan0: authenticated
[   51.281783] wlan0: associate with AP 00:24:17:31:cc:b3
[   51.284661] wlan0: RX AssocResp from 00:24:17:31:cc:b3 (capab=0x411 status=0 aid=2)
[   51.284665] wlan0: associated
[   51.321628] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   61.480006] wlan0: no IPv6 routers present
[  123.377963] wlan0: disassociating by local choice (reason=3)
[  135.759137] wlan0: direct probe to AP 00:24:17:31:cc:b3 try 1
[  135.950020] wlan0: direct probe to AP 00:24:17:31:cc:b3 try 2
[  136.150024] wlan0: direct probe to AP 00:24:17:31:cc:b3 try 3
[  136.350017] wlan0: direct probe to AP 00:24:17:31:cc:b3 timed out
```The last 4 lines of this just loop for ages

```
lshw -C network

-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:26:18:58:c3:2e
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.65 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:e800(size=256) memory:f8fff000-f8ffffff(prefetchable) memory:f8fe0000-f8feffff(prefetchable) memory:febf0000-febfffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:b0:8c:02:02:c4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

```kernel 2.6.31-14-generic x86_64

I can connect via ethernet fine. Thanks in advance for any help

---

### Post by amacus on 2009-11-02
Fixed this by adding this

#Try to fix wireless
blacklist rt2800usb
blacklist rt2870sta

to

/etc/modprobe.d/blacklist.conf

No idea what it does though

---

