---
title: "Ubuntu 9.10 With Belkin Wireless USB Stopped Working"
date: 2011-06-29
forum: Networking &amp; Wireless
---

### Post by Haltini on 2011-06-29
*Edit: I'm noticing that this thread has gotten a fair few views but no responses, I'm now wondering if I have a really obscure problem that no one knows how to fix. It wouldn't be the first. As a result could someone let me know if they have a look through the problem and don't know what the problem is as that would also be useful information. Thanks.*


Hi,

After running Ubuntu 9.10 with my wireless connection for the past 9 months it decided to stop working. It still works on a live CD however (Mint Julia), so I'm pretty certain it isn't a hardware problem. I have posted all of the information requested in the HOWTO thread.

I can still see the networks however I can not connect to them.

Any help would be appreciated.
Thanks.
-Matthew

**1 )** **Machine Brand and Model (PC/Laptop)**
PC I built myself.

**2 ) ****Wireless Brand, Model and Wireless Chipset**

```
lsusb -v
```gives:

```

Bus 002 Device 002: ID 050d:705e Belkin Components 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x050d Belkin Components
  idProduct          0x705e 
  bcdDevice            2.00
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           81
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          4 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           9
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              2 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
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
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x07  EP 7 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x89  EP 9 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0a  EP 10 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0b  EP 11 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x0c  EP 12 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)
```**3 ) ****check interface**
ifconfig

```
wlan0     Link encap:Ethernet  HWaddr 00:1c:df:46:07:ac  
          inet6 addr: fe80::21c:dfff:fe46:7ac/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2373 (2.3 KB)  TX bytes:2629 (2.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-DF-46-07-AC-34-36-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```iwconfig

```
wlan0     IEEE 802.11bg  Mode:Managed  Frequency:2.457 GHz  
          Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```**4 ) **[B]Check for modules
[/B]
```
lsmod | grep "lan"
```returns nothing

**5 ) Kernel boot messages**

```
dmeg | grep "wlan"
```returns:

```
[   15.891077] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.891208] bridge-wlan0: device is wireless, enabling SMAC
[   15.891216] bridge-wlan0: up
[   15.891218] bridge-wlan0: attached
[   15.904759] bridge-wlan0: disabling the bridge
[   15.920517] bridge-wlan0: down
[   15.920523] bridge-wlan0: detached
[   59.345758] wlan0: authenticate with AP 00:14:6c:ab:06:7a
[   59.347880] wlan0: authenticated
[   59.347883] wlan0: associate with AP 00:14:6c:ab:06:7a
[   59.350391] wlan0: RX AssocResp from 00:14:6c:ab:06:7a (capab=0x431 status=0 aid=1)
[   59.350395] wlan0: associated
[   59.355968] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   62.351481] wlan0: deauthenticated (Reason: 2)
[   63.348020] wlan0: direct probe to AP 00:14:6c:ab:06:7a try 1
[   63.552514] wlan0: direct probe to AP 00:14:6c:ab:06:7a try 2
[   63.748015] wlan0: direct probe to AP 00:14:6c:ab:06:7a try 3
[   63.750524] wlan0 direct probe responded
[   63.750527] wlan0: authenticate with AP 00:14:6c:ab:06:7a
[   63.752514] wlan0: authenticated
[   63.752519] wlan0: associate with AP 00:14:6c:ab:06:7a
[   63.755021] wlan0: RX ReassocResp from 00:14:6c:ab:06:7a (capab=0x431 status=0 aid=1)
[   63.755025] wlan0: associated
[   69.468506] wlan0: no IPv6 routers present
[   76.087077] wlan0: disassociating by local choice (reason=3)
[   88.729262] wlan0: authenticate with AP 00:14:6c:ab:06:7a
[   88.928019] wlan0: authenticate with AP 00:14:6c:ab:06:7a
[   89.128016] wlan0: authenticate with AP 00:14:6c:ab:06:7a
[   89.129563] wlan0: authenticated
[   89.129566] wlan0: associate with AP 00:14:6c:ab:06:7a
[   89.132812] wlan0: RX AssocResp from 00:14:6c:ab:06:7a (capab=0x431 status=0 aid=1)
[   89.132816] wlan0: associated
[   92.134032] wlan0: deauthenticated (Reason: 2)
[   93.136514] wlan0: direct probe to AP 00:14:6c:ab:06:7a try 1
[   93.139284] wlan0 direct probe responded
[   93.139287] wlan0: authenticate with AP 00:14:6c:ab:06:7a
[   93.141521] wlan0: authenticated
[   93.141524] wlan0: associate with AP 00:14:6c:ab:06:7a
[   93.144025] wlan0: RX ReassocResp from 00:14:6c:ab:06:7a (capab=0x431 status=0 aid=1)
[   93.144028] wlan0: associated
[   97.065349] wlan0: deauthenticated (Reason: 2)
[   99.068016] wlan0: direct probe to AP 00:14:6c:ab:06:7a try 1
[   99.070588] wlan0 direct probe responded
[   99.070590] wlan0: authenticate with AP 00:14:6c:ab:06:7a
[   99.072829] wlan0: authenticated
[   99.072833] wlan0: associate with AP 00:14:6c:ab:06:7a
[   99.075335] wlan0: RX ReassocResp from 00:14:6c:ab:06:7a (capab=0x431 status=0 aid=1)
[   99.075338] wlan0: associated
[  102.122811] wlan0: deauthenticated (Reason: 6)
[  103.120020] wlan0: direct probe to AP 00:14:6c:ab:06:7a try 1
[  103.123048] wlan0 direct probe responded
[  103.123052] wlan0: authenticate with AP 00:14:6c:ab:06:7a
[  103.124556] wlan0: authenticated
[  103.124560] wlan0: associate with AP 00:14:6c:ab:06:7a
[  103.127668] wlan0: RX ReassocResp from 00:14:6c:ab:06:7a (capab=0x431 status=0 aid=1)
[  103.127671] wlan0: associated
[  108.807199] wlan0: deauthenticated (Reason: 6)
[  109.804017] wlan0: direct probe to AP 00:14:6c:ab:06:7a try 1
[  109.806575] wlan0 direct probe responded
[  109.806579] wlan0: authenticate with AP 00:14:6c:ab:06:7a
[  109.808686] wlan0: authenticated
[  109.808688] wlan0: associate with AP 00:14:6c:ab:06:7a
[  109.811196] wlan0: RX ReassocResp from 00:14:6c:ab:06:7a (capab=0x431 status=0 aid=1)
[  109.811198] wlan0: associated
[  112.814676] wlan0: deauthenticated (Reason: 2)
[  113.812020] wlan0: direct probe to AP 00:14:6c:ab:06:7a try 1
[  113.815030] wlan0 direct probe responded
[  113.815035] wlan0: authenticate with AP 00:14:6c:ab:06:7a
[  113.816663] wlan0: authenticated
[  113.816669] wlan0: associate with AP 00:14:6c:ab:06:7a
[  113.819776] wlan0: RX ReassocResp from 00:14:6c:ab:06:7a (capab=0x431 status=0 aid=1)
[  113.819779] wlan0: associated
[  116.540986] wlan0: disassociating by local choice (reason=3)
[ 1576.751378] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```**6 ) Network configuration**

```
sudo lshw -C network
```gives:

```
  *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:fb:0e:e0
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:fe9c0000-fe9fffff ioport:dc00(size=128)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:df:46:07:ac
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```**7 ) Scan for networks**

```
iwlist scan | grep "wlan"
``` gives:

```
wlan0     No scan results
```[B]

8 ) Ubuntu version[/B]

```
Description:    Ubuntu 9.10
```[B]

9 ) Kernel/architecture (including 32 vs. 64 bit)
[/B]
```
uname -mr
```gives:

```
2.6.31-14-generic i686
```[B]

10 ) Restarting the network[/B]

Certainly didn't fix the problem but

```
 sudo /etc/init.d/networking restart
```returned:

```
 * Reconfiguring network interfaces...                                   [ OK ]
```

---

### Post by Haltini on 2011-06-29
I forgot to mention that I can still see all the different networks, I  just can't connect to them, which is probably important so I've added it  to the OP.

---

### Post by Haltini on 2011-06-30
I'm now wondering if I have a really obscure problem that no one knows how to fix (the reason I'm still on Karmic). Would be nice to know if this is the case and have updated the OP with this request.

If I get no replies this will be my last bump.

Thanks in advance.
-Matthew

---

