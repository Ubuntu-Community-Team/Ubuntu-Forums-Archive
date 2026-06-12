---
title: "edimax ew-7318UG wireless on ubuntu 8.10 problems"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by danatom on 2009-07-19
I'm having a lot of problems getting wifi working on my ubuntu 8.10 machine. I started with another wireless usb device which wasn't working, so I have just bought the Edimax ew-7318UG dongle, but it's still not working.

I have previously tried using ndiswrapper, wcid and the native support for this device. As none of this was working, I downloaded and compiled the latest driver (1.0.3.6) from the CVS repository on serialmonkey.com and installed it.

lsusb | grep RT:

```
Bus 005 Device 004: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
```lsmod | grep rt:
```

rt73usb                30464  0 
crc_itu_t              10112  1 rt73usb
rt2x00usb              18816  1 rt73usb
rt2x00lib              36224  2 rt73usb,rt2x00usb
rfkill                 17048  1 rt2x00lib
led_class              12164  1 rt2x00lib
mac80211              216820  2 rt2x00usb,rt2x00lib
cfg80211               32392  2 rt2x00lib,mac80211
rt73                  226176  1 
parport_pc             39332  1 
parport                42604  3 ppdev,lp,parport_pc
iTCO_vendor_support    11652  1 iTCO_wdt
agpgart                42184  3 drm,intel_agp
usbcore               149488  7 rt73usb,rt2x00usb,rt73,usbhid,ehci_hcd,uhci_hcd
```dmesg:

```
[ 1913.480033] usb 5-7: new high speed USB device using ehci_hcd and address 6
[ 1913.751551] usb 5-7: configuration #1 chosen from 1 choice
[ 1913.751953] rt73: idVendor = 0x148f, idProduct = 0x2573 
[ 1913.753844] firmware: requesting rt73.bin
[ 1913.943372] rt73: using permanent MAC addr
[ 1913.943389] rt73: Active MAC addr: *******
[ 1913.943394] rt73: Local MAC = *******
[ 1917.972441] rt73: driver version - 1.0.3.6 CVS
[ 1918.004497] rt73: using net dev supplied MAC addr
[ 1918.004511] rt73: Active MAC addr: *******
[ 1918.004517] rt73: Local MAC =*******
[ 1928.992018] wlan0: no IPv6 routers present
```/etc/modprobe.d/blacklist (subset):

```
blacklist rt2x00lib
blacklist rt2x00pci
blacklist rt2x00usb
blacklist rt61pci
blacklist rt73usb
blacklist rt2400pci
blacklist rt2500pci
blacklist rt2500usb
```sudo lshw -C network:

```
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: *********
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN
```iwlist scan:

```
wlan0     Scan completed :
          Cell 01 - Address: *********
                    ESSID:"BeBox"
                    Mode:Managed
                    Channel:11
                    Encryption key:off
                    Bit Rates:0 kb/s
```iwconfig:

```
wlan0     RT73 WLAN  ESSID:"BeBox"  
          Mode:Managed  Frequency=2.462 GHz  Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level:-52 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```ifconfig:

```
wlan0     Link encap:Ethernet  HWaddr ********  
          inet6 addr: ********/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9675 (9.6 KB)  TX bytes:1756 (1.7 KB)
```cat /etc/network/interfaces:

```
auto lo
iface lo inet loopback

```This is everything I can think of to try and illustrate the problem. I have switched off all encryption to try and get this to work, but it refuses to connect. I am using the network manager to try and connect and it just tries and tries and fails.

I cannot ping my router, so have no connection on the network at all, any help would be much appreciated.

Thanks,
Dan

---

