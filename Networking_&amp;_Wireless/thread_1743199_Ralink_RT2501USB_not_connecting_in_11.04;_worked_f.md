---
title: "Ralink RT2501USB not connecting in 11.04; worked fine in 10.04"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by scialen on 2011-04-29
I added a post a day ago, but I didn't follow the guidelines for an effective post, so sorry for that. Here's the full details that I can give you:

The Ralink RT2501USB wireless connects fine with the default drivers in Ubuntu 10.04, but this does not seem to be the case for 11.04. All that happens is 'wireless not connected', despite there being a list of active wireless networks to connect to.

The following are outputs from 11.04:

1) **Computer model: **Advent 7204

2) **lsusb | grep 'Ralink'**
```

Bus 001 Device 004: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter

```3) **iwconfig wlan0**
```

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```4)  **lsmod | grep rt**
```

parport_pc             32111  0 
rt73usb                26854  0 
rt2500usb              22621  0 
rt2x00usb              19693  2 rt73usb,rt2500usb
rt2x00lib              39075  3 rt73usb,rt2500usb,rt2x00usb
mac80211              257001  2 rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
parport                36746  3 parport_pc,ppdev,lp
crc_itu_t              12627  3 udf,rt73usb,firewire_core

```5)  **dmesg | grep wlan0**
```

[   14.995615] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.354764] wlan0: authenticate with 00:1c:df:9b:cb:eb (try 1)
[   30.356284] wlan0: authenticated
[   30.375793] wlan0: associate with 00:1c:df:9b:cb:eb (try 1)
[   30.378313] wlan0: RX AssocResp from 00:1c:df:9b:cb:eb (capab=0x431 status=0 aid=1)
[   30.378318] wlan0: associated
[   30.391269] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   40.464034] wlan0: no IPv6 routers present
[   77.229399] wlan0: deauthenticating from 00:1c:df:9b:cb:eb by local choice (reason=3)

```6) **sudo lshw -C network**
```

*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:66:db:a0
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:2000(size=256) memory:b0200c00-b0200cff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:10:60:a0:53:aa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.38-8-generic firmware=1.7 link=no multicast=yes wireless=IEEE 802.11bg

```7) **iwlist scan**
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

```8 ) **lsb_release -d**
```

Description:    Ubuntu 11.04

```9) **uname -mr**
```

2.6.38-8-generic i686

```10) **sudo /etc/init.d/networking restart**
```

 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 

```

---

### Post by scialen on 2011-04-29
I've switched back to 10.04 for now, and when available I will try 11.04 with a wired connection and see if internet is AT ALL possible.

I'll run some more tests and try things out. I'll let you all know how it goes!

Sorry again for the two threads!

---

### Post by Marco.75 on 2011-05-04
same interface same exact problem... everything was fine in 10.04... in 10.10 and 11.04 I see wireless networks but for same reason I can't connect.

---

### Post by ebrato on 2011-05-05
type:
sudo iwconfig wlan0 power off

i'm new one in ubuntu and linux but i found this solution on some german ubuntu forum and it works for me, but i don't know how turn it on every time while system starting

EDIT:
i putted command "iwconfig wlan0 power off" without "sudo" to /etc/rc.local ("sudo gedit /etc/rc.local") 
answer is it work for you?

---

