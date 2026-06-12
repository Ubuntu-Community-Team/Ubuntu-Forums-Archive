---
title: "Lost wireless all of a sudden. Hardware or software issue?"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by frsswdn on 2011-07-01
Hi,

I was surfing the internet happily yesterday when all of a sudden wireless internet stopped working and the netbook seems kind of frozen. Tried to reboot to discover that I cannot turn my wireless on with the keyboard buttons anymore. Tried google and searching different forms in vain. I gathered some diagnosis along the way posted below, but I am starting to wonder whether this is a hardware or a software failure. I suspect it to be a hardware issue as it happened out of the blue, but I am not sure how to check that out. Any ideas?

The dmesg output has some hints, but googling it did not give any clues about what is going on.

```

laptop:~$ dmesg | grep rt
[B][   13.033006] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[   13.033026] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.[/B]
[   13.033208] usbcore: registered new interface driver rt2500usb
[   13.946559] Registered led device: rt73usb-phy1::radio
[   13.946767] Registered led device: rt73usb-phy1::assoc
[   13.946969] Registered led device: rt73usb-phy1::quality
[   13.949829] usbcore: registered new interface driver rt73usb


```

```

laptop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:25:c9:00:0b:d2
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.42.43.10 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:50010000-50010fff memory:50000000-5000ffff memory:50020000-5002ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       bus info: usb@1:5
       logical name: wlan0
       serial: 00:18:1a:0b:05:9e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg


```

```

laptop:~$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1267:0201 Logic3 / SpectraVideo plc A4Tech SWOP-3 Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter
Bus 001 Device 003: ID 0ac8:3420 Z-Star Microelectronics Corp. Venus USB2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

```

laptop:~$ lsmod | grep rt
parport_pc             32111  0 
rt73usb                26854  0 
crc_itu_t              12627  1 rt73usb
rt2500usb              22621  0 
rt2x00usb              19693  2 rt73usb,rt2500usb
rt2x00lib              39075  3 rt73usb,rt2500usb,rt2x00usb
mac80211              257001  2 rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
parport                36746  3 parport_pc,ppdev,lp


```

```

laptop:~$ uname -a
Linux laptop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux


```

---

### Post by nm_geo on 2011-07-01
You may be in luck I found a link where chili was helping people with 
rt2500usb and rt73usb conflicts.

[http://ubuntuforums.org/showthread.php?t=1742267](http://ubuntuforums.org/showthread.php?t=1742267)

I am not familiar with this but if chili555 recommends something I listen.

blacklisting is easy to do and to fix if it does not work.

It does appear you have a conflict between the two.

---

### Post by chili555 on 2011-07-01
> [   13.033006] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[   13.033026] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.This strongly suggests that too many drivers are loading. Both rt73usb and rt2500usb load and probably conflict. Let's blacklist rt2500usb and reboot and see if things improve. Please do:```
sudo su
echo "blacklist rt2500usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and give us your report. If it's not working, post:```
dmesg | grep rt
rfkill list all
```What kind of computer is it?

---

### Post by chili555 on 2011-07-01
> **nm_geo said:**
> You may be in luck I found a link where chili was helping people with 
rt2500usb and rt73usb conflicts.

[http://ubuntuforums.org/showthread.php?t=1742267](http://ubuntuforums.org/showthread.php?t=1742267)

I am not familiar with this but if chili555 recommends something I listen.

blacklisting is easy to do and to fix if it does not work.

It does appear you have a conflict between the two.You are fast tonight! No second glass of adult beverage for me!

---

### Post by nm_geo on 2011-07-01
> **chili555 said:**
> You are fast tonight! No second glass of adult beverage for me!

Well i will take your adult beverages I need um..

---

### Post by frsswdn on 2011-07-01
Hi guys,

thanks for the help. It actually worked! Blacklisting rt2500usb.

One thing to note though, the keyboard key does not turn the wireless on. Now it just changes the hw state as reported by rfkill. One needs to go to the Network Manager and manually select Enable Wireless. I am sending this reply from the wireless network.

I am curious though about the posts in 
[http://ubuntuforums.org/showthread.php?t=1742267](http://ubuntuforums.org/showthread.php?t=1742267)

I also noticed before that my wifi on the netbook is very slow and often hanfs (I have another laptop running fedora where the wifi is much faster and does not hang). Was wondering if the recommendation on the other thread of doing 

sudo modprobe rt73usb nohwcrypt=1

Could provide help with the slowness?

I am also pretty puzzled how this problem popped up all of a sudden without doing any software updates or the like???

---

### Post by frsswdn on 2011-07-01
it is a belco netbook, bought in china two years ago (I could not find anything similar anywhere else in the world while travelling all around for the last 2 years. It was very economical option.)

---

### Post by chili555 on 2011-07-01
> Was wondering if the recommendation on the other thread of doing

sudo modprobe rt73usb nohwcrypt=1

Could provide help with the slowness?You're the one with the device. Please try it and report.

You could also amend the blacklist file to change the blacklist to rt73usb and let rt2500usb drive your device and see if it works better. Again, give us your report so the searchers will learn from your experience.> it is a belco netbook, bought in china ...It was very economical option.I haven't any ideas; I am not familiar with this brand and it's quirks. Many well-known  laptops have quirks, by the way.

---

### Post by frsswdn on 2011-07-01
blacklisting rt73usb results in no wifi, and the same error massages in the dmesg as reported in first post. So for me rt73usb seems to be the right driver. I am working now with the nohwcrypt=1. I will probably need some time to try and figure out what differences it has, if at all.

As for the belco netbook, I am pretty happy with it. It has in my opinion a high quality / price ratio. The only thing that got missed up with ubunut 11.04 is the unity starting thing, where I need to go to a terminal ctr+alt+f1 and start unity manually, or alternatively go to classic. I read some posts on how one needs to set the screen resolution in the kernel options, but did not have much time to play with it.

---

