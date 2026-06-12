---
title: "Ndiswrapper &amp; Bradcomm BCM4306"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by ruddyrum on 2010-04-19
OK, so i have installed ndiswrapper, and the correct drivers for the wireless card.

```
ndiswrapper -l:
bcmwl5a : driver installed
    device (14E4:4320) present  
```I seemed to be having a conflict with the generic drivers which loaded for my wifi device 'b43-pci-bridge' and the ndiswrapper drivers i installed.

So i ran the command 'rmmod ssb' and now my broadcomm wireless device is "unclaimed"

```

lshw -C Network:
***-network:0 UNCLAIMED**
       description: Network controller
       product: BCM4306 802.11g Wireless LAN Controller
       vendor: Broadcomm Corp.
       physical id: 3
       bus info: pci@0000:01:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       configuration: latency=168
       Resources: memory:24000000-24001fff

```then ran 'modprobe ndiswrapper' to try and load it, but the network device is still unclaimed.

I ran 'echo 'ndiswrapper' | sudo tee -a /etc/modules' to have it load ndiswrapper on boot, but it still loads the generic driver, and i have to unclaim it manually... however i can not get ndiswrapper to load the driver once it is unclaimed.

Also, under both ifconfig & iwconfig, i have no wlan0 device... anyway i can add one manually??

Any help is much appreciated!

---

### Post by 2hot6ft2 on 2010-04-19
You might want to check this to see what you're missing.
[The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")

Perhaps blacklist the b43 driver.
```
gksu gedit /etc/modprobe.d/blacklist.conf
```

Sounds like you know your way around the system so you should be able to figure out what the problem is between those two.

---

