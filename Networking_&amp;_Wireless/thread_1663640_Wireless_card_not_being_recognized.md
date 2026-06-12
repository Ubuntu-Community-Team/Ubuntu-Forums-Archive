---
title: "Wireless card not being recognized"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by sbaig on 2011-01-09
Hi,

I have lucid installed on my hp laptop without any problems, and I went to install it on another hp but the I can't connect to any wireless network.
 I tried to follow this thread's advice[ http://ubuntuforums.org/showthread.php?t=1638660]("http://ubuntuforums.org/showthread.php?t=1638660") . Because it's pretty much the same problem except I think the wireless card is from a different Intel family but it didn't work.

Basically wireless networks won't show up, in fact the network icon only has "wired" as a menu option.

I tried to follow the thread, even though I had no idea what it was saying as far as instruction goes.

---

### Post by Bucky Ball on 2011-01-09
Plug in an ethernet cable. With a HP machine that should fix it. Get your updates, you may even be offered the correct firmware/drivers. Go to System >Admin >Additional Drivers. What's there? If you need to activate the wireless drivers from there you need to be online to download them.

WARNING: If you are installing a recent 10.10 release there are known problems and consequent bug reports concerning Broadcom cards. Quite a few HP machines use the very cards. I would advise trying with the previous kernel if you are using this one (you will see by the numbers at the end of the entry at your grub list at boot:

2.6.35-24

If you're using this it is probably part of the problem. BUT, get online and do as I mentioned first to be sure. These problems are not occuring with that kernel on all machines (I'm running it now).

Also, open a terminal (Applications >Accessories >Terminal) and past this in:

```
sudo lshw -C network
```Copy, paste, and post the output here.

---

### Post by sbaig on 2011-01-10
It won't go online even with the ethernet plugged in so I can't look up the drivers.

here's the output:
> rasha@rasha-laptop:~$ sudo lshw -C network
[sudo] password for rasha: 
  *-network               
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:d8500000-d8503fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:b0:6f:c4
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=no multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:3000(size=256) memory:d2410000-d2410fff(prefetchable) memory:d2400000-d240ffff(prefetchable) memory:d2420000-d243ffff(prefetchable)


---

### Post by Bucky Ball on 2011-01-10
Hmm. Pity cos that wireless card should work out of the box with two clicks, but you need to be online to download the drivers and firmware. Catch 22.

This could help:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

The STA driver can be installed with NO internet access. The b43 needs access to a computer with internet access for you to download software to a dongle (obviously not the machine you're working on or you wouldn't need to do all this!). Generally, one of these drivers works better than the other for any particular card. You don't install both. One or the other.

---

### Post by sbaig on 2011-01-11
so .. umm lol what should i do? I don't know why it won't go online with the ethernet cable.

---

### Post by sbaig on 2011-01-11
ok well the link you sent me, has insturctions for both STA and b43 but it also has ways to install either driver offline as well.

But my question is. which one should I install?

---

### Post by Bucky Ball on 2011-01-11
As mentioned, you need access to a computer that is online and a dongle to download and transfer data to the machine you are working on for b43.

STA is all on the install disk by the looks of it. (unless it's the other way around; check the link for that).

It's really pot luck. You would need to do some research. b43 is best for some people with some rigs and cards, STA for others. Trial and error. b43 worked great for me when I was using a HP. ;)

---

### Post by sbaig on 2011-01-11
ok but will this also fix the problem with the wired connection? is it that i don't have drivers for both devices?

---

### Post by Bucky Ball on 2011-01-11
Just going back through this thread: what release are you using? I can't see that you've mentioned. If it is 10.10, stop now. That has issues with Broadcom at the moment and could very well be your problem.

I would go with 10.04 LTS or boot into the previous kernel (third on the list), 2.6.35-23 and see if you get more joy. -24 is kinda screwed on some setups for now. ;)

---

### Post by sbaig on 2011-01-11
:o . I meant to write it .sorry I forgot to mention it, Im using 10.04 32bit.

---

### Post by Bucky Ball on 2011-01-11
On a 64bit machine?

---

### Post by sbaig on 2011-01-11
No, on a 32 bit. See I would go ahead and install the STA drivers b/c the device is supported (BCM4322) but I would also like to be able to use my ethernet connection too.

---

### Post by Bucky Ball on 2011-01-11
You did switch machine off, plug cable in, then reboot? I know this sounds really peculiar, but some people have been having some success by unplugging everything from the machine for 30 minutes - battery, power, mice, everything.

I know, sounds like a goblin's spell but it really has worked to get people's cable connection up. Damned weird but can't argue with fact I guess.

Also, at this point, doesn't matter which you get up; being online on the machine your working on is going to help to fix things more easily (whether that be getting cable up or wireless).

---

### Post by sbaig on 2011-01-11
hmm well ok its a laptop so the only thing to remove i guess is the powercable and battery. I'll go ahead and install the STA drivers since that seems to be the only ones that support my device.

---

