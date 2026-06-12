---
title: "Last time wireless worked out of the box was in 9.04. Now it doesn't work."
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by wookieeface on 2010-04-30
Wireless hasn't been working in the last two (9.10 and 10.04) kubuntu  versions. In everything from 6.06 to 9.04 it worked flawlessly out of  the box. But on the 9.10 live cd it didn't work, neither did it work  when I installed it, so I chose to roll back to 9.04 an wait for 10.04  to see if it would work now. But it still doesn't.

When I right click on network manager in the system tray the option to  "Enable wireless" is greyed out.

The pc I'm running it on is a 7-8 years old Medion MD8383, and  apparently the wireless card has a Ralink chipset, and seems to be set  as a usb device, and not a pci device, even though it's internal. (But  it's the same both in the versions of kubuntu it works in, and those in which it  doesn't.)

When I run lsusb I get the following (only the relevant line):
```
Bus  001 Device 004: ID 148f:2570 Ralink Technology, Corp. 802.11g  WiFi
```Running iwconfig I get this:
```
 lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
pan0      no wireless extensions.

```And ifconfig:
```
 eth0      Link encap:Ethernet  HWaddr 00:11:09:a3:cb:b3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000                                                                                                                                          
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18                                                                                                                                                          

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11232 (11.2 KB)  TX bytes:11232 (11.2 KB)

```Then I ran "lsmod | grep "rt"", because I'm pretty sure that's the wifi  module:
```
 rt2500usb              18141  0                                                                                                                                                     
rt2x00usb               9703  1 rt2500usb                                                                                                                                           
rt2x00lib              27509  2 rt2500usb,rt2x00usb                                                                                                                                 
led_class               2864  1 rt2x00lib                                                                                                                                           
mac80211              204922  2 rt2x00usb,rt2x00lib                                                                                                                                 
agpgart                31724  3 ttm,drm,intel_agp                                                                                                                                   
parport_pc             25962  1                                                                                                                                                     
cfg80211              126485  2 rt2x00lib,mac80211                                                                     
parport                32635  3 ppdev,parport_pc,lp   

```And here are the lines I'd think are relevant from dmesg:
```
 [    8.808116] Registered led device: rt2500usb-phy0::radio
[    8.808153] Registered led device: rt2500usb-phy0::quality
[    8.808661] usbcore: registered new interface driver rt2500usb
[   12.865464] ADDRCONF(NETDEV_UP): wlan0: link is not ready


```And then at last I ran "sudo lshw -C network"
```
   *-network               
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 8b
       serial: 00:11:09:a3:cb:b3
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:18 ioport:d300(size=256) memory:d8003000-d80030ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:09:51:4c:94
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```But well, I hope someone can help me with this!
And I've got both 10.04 and 9.04 installed on the same machine, so I can  compare stuff between them if needed.

---

### Post by wookieeface on 2010-05-01
bump

---

