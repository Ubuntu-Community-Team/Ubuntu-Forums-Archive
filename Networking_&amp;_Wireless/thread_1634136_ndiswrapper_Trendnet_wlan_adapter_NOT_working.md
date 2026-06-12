---
title: "ndiswrapper Trendnet wlan adapter NOT working"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by cromestant on 2010-11-30
Hello,
I posted yesterday but post apparently did not get posted, or was moderated but I was not informed.
Anyway here is more info
WIFI usb adapter by trendnet  TEW-648UB
Apparently detected but did not work.
installed the provided windows drivers with ndiswrapper and all seems to be fine:
```
cromestant@cromestant-IMEDIA-D3610-FR:~$ ndiswrapper -l
net8192su : driver installed
	device (0BDA:8171) present (alternate driver: r8192s_usb)

```
and alternate driver is blacklisted :
```
cromestant@cromestant-IMEDIA-D3610-FR:~$ cat /etc/modprobe.d/blacklist.conf 
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

[snip]

blacklist ssb
blacklist r8192s_usb

```

now I still don't see the networks so I did:
```
sudo depmod -a

```
with no errors
and also
```
cromestant@cromestant-IMEDIA-D3610-FR:~$ sudo modprobe ndiswrapper 
```
now I have
```
cromestant@cromestant-IMEDIA-D3610-FR:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"p\xE9>\xA1A\xE1\xFCg>\x01~\x97\xEA\xDCk\x96\x8F8\*\xEC\xB0;\xFB2\xAF<T\xEC\x18\xDB\"  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
still no networks and finally
```
cromestant@cromestant-IMEDIA-D3610-FR:~$ sudo lshw -C Network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:21:97:a4:4c:39
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.10 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:e800(size=256) memory:febff000-febfffff memory:febc0000-febdffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:d1:e5:6b:68
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=802.11b/g

```

what is odd is this DISABLED flag in there...

what else can I do to get this to work?

thank you in advance for your help

---

### Post by cromestant on 2010-11-30
rebooted and it worked... still don't get it.. but am happy, 
tested and working on WPA personal network

---

### Post by walt.smith1960 on 2010-11-30
Have you tried a suspend/resume cycle yet?  I started a thread about a TEW-649 and NdisWrapper.  It installed and works great.  It suspends fine but doesn't want to un-suspend. Unplugging and re-plugging fixes the problem.  I'm curious whether your device's power management works correctly.

---

### Post by cromestant on 2010-11-30
Well I'm on a desktop, so maybe this works differently

But I tested it, suspended from menu, and then restored, the device and connection were properly restored.

---

### Post by znuxor on 2011-01-22
It is working. :D
Thank you
I tried to install that wireless key but it wasn't working with the "official" driver code on the realtek website.

Edit: Apparently, it is a temporary fix. It isn't working now.

---

