---
title: "BCM4306 (rev03) on a Compaq Presario R3000"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by Bryan76 on 2009-12-16
I'm having difficulties getting the BCM4306 (rev03) working.  Here are some relevant details:

lspci  -n |grep '14e4'
```

02:02.0 0280: 14e4:4320 (rev 03)

```lspci |grep -e Network -e Ethernet
```

00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```lsmod |grep -e ndiswrapper -e b43 -e bcm
```

b43legacy             117752  0 
b43                   122136  0 
mac80211              181076  2 b43legacy,b43
cfg80211               93052  3 b43legacy,b43,mac80211
led_class               4096  2 b43legacy,b43
ssb                    35300  2 b43legacy,b43

```Note:  I've tried with both the b43legacy module and without, neither have worked

dmesg |grep b43
```

[    1.787071] b43-pci-bridge 0000:02:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.989770] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   20.148048] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   20.273986] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   20.300886] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   20.363680] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   20.552049] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   20.636808] Registered led device: b43-phy0::tx
[   20.636837] Registered led device: b43-phy0::rx
[   20.636867] Registered led device: b43-phy0::radio

```So it appears that the b43 driver is loading properly.

Now here's where things get interesting:

sudo lshw -c network
```

  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:18 memory:d0204000-d0205fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:4c:60:da
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=67.108.161.236 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:19 ioport:a000(size=256) memory:d0208800-d02088ff
  *-network
       description: [COLOR=Red]Wireless interface[/COLOR]
       physical id: 3
       [COLOR=Red]logical name: wlan0[/COLOR]
       serial: 00:90:4b:a8:b6:07
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```What's this?  A *second* wireless card that shares the same physical id as the Realtek card (the wired ethernet card).  Does this Realtek ethernet card also have a wireless radio in it?  Does this laptop have two radios?  Why is wlan being assigned to this second card and not the BCM4306?  If this is a second wireless card, and that's what's causing the problems, can I disable the wireless portions of the Realtek card while keeping the wired portions active?

Oh, and of course I'm running karmic.


Thanks all!

---

### Post by billfinch on 2009-12-17
I had lots of grief with the same config on a Presario M2000. Here's my post on how to solve it. I never really tried that hard with Karmic, but the principles are the same

Finally....

I got it going and here's how. First I went back to 8.04 Hardy. 9.10 Karmic wouldn't play nice.

First, it is imperative to get the right Win Driver, as all have noted. This is not trivial, as it appears BCM made a config du jour for the PC manf. I found the right one for my rev 03 card on the Compaq support site, not the HP support site. sp29361 for M2000 Presario.

I expamded this thing on my PC and copied the bcmwl5.inf and bcmwl5a.inf plus bcmwl5.sys to the Ubuntu machine into my user folder.

Then the technique is fairly simple. Thanks to Dapperme17 for the basics..You have to make sure the b43 and ssb modules are removed. I removed ndiswrapper as it was being loaded by somebody and I wanted a clean slate.

sudo rmmod b43
sudo rmmod ssb
sudo rmmod ndiswrapper


Installed the ndis gtk from the repository. I wanted to see what drivers I really was loading. Navigated to /home/bill/driver folder and selected both 5 and 5a as I wasn't sure what the significance of the "5a" was. No complaints, so I checked with lshw after doing a network restart. Everything looked clean and I had ndiswrapper re-installed.

sudo /etc/init.d/networking restart
sudo lshw -C network

I saw the ndiswrapper+bcmwl5 as the driver used. No lights, so I tried the switch and damn if it didn't turn on and connect! As stated in other posts it is easy to lose track of where the hardware switches are set.

To make this permanent, I created a shell script to run at start up based on help from dmizer among others.

Here's the code. I called my script wireless.sh.

sudo gedit /etc/init.d/wireless.sh

then write the script....

#!/bin/bash

sudo rmmod b43
sudo rmmod ssb
sudo rmmod ndiswrapper
modprobe ndiswrapper

Thats it. Save it. Now you have to make the script executable and update yet another file, rc.d.

sudo chmod +x /etc/init.d/wireless.sh
sudo update /etc/rc.d/ wireless.sh start s 50 .

The dot is important. Terminal should tell you the rcS has been updated

Reboot and it should all work.

This only took 3 weeks and there are probably a zillion things that could go wrong between distros and hardware and all. One thing for sure. b43 and ssb DO NOT WORK with the 4306 rev 03.

Good luck....:)

---

### Post by dcoats on 2009-12-30
You do want the b43 driver and it does work fine with that card.
```
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
        Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:12f4]                                        
        Flags: bus master, fast devsel, latency 64, IRQ 18                                                            
        Memory at d0204000 (32-bit, non-prefetchable) [size=8K]                                                       
        Kernel driver in use: b43-pci-bridge    
``` 
works 100% here and has for ages.
Please see [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

