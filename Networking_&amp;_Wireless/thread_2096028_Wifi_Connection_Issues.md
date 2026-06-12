---
title: "Wifi Connection Issues"
date: 2012-12-18
forum: Networking &amp; Wireless
---

### Post by DrNugget on 2012-12-18
Ok, so I'm a bit new to Ubuntu. I'm loving it so far: it's fast, good looking, and so far compatible with all the hardware in my desktop. there's just one issue: i have a d-link airplus xtreme g dwl-520 wifi card. Yeah, i know, it came out in 2004. I'm getting a new one soon. Anyway, it finds my wifi right away, but for whatever reason the network keeps kicking me; it'll automatically disconnect if i try to do anything on the internet. then it'll keep trying to reconnect but it never keeps the connection longer than a few seconds. A popup keeps coming up, asking me for the network password, which I enter, it connects for a second, disconnects, reconnects, and asks me for the password again.I looked up the driver for this wifi card, but because it's so old, the driver was no longer posted on d-link's website. i thought i might be able to install WINE, (connection works just fine from my netbook running windows 7 starter) but for that i need an internet connection that works. it's a catch 22. anyways, if there's anyone who might be able to offer a spot of help, i would appreciate it.

---

### Post by Bucky Ball on 2012-12-18
*Thread moved to **Networking & Wireless***

Welcome to the forums. Don't worry, they'll be gentle here,too, and you'll have a better chance of getting help.

You definitely DON'T want to install Wine for this issue. Disrelated. Your card is working fine as it is connecting but then dropping off so driver probably fine and another problem. Could you open a terminal with Applications>Accessories>Terminal, and copy/paste this in:
```

sudo lshw -C network
```With the card in. Post the result back here please.

PS: Please use paragraphs rather than blocks of text. Hard to read and reduces your chances of help (some will find it impossible to read for various reasons and others just won't be bothered. Cheers. ;))

PPS: Have you done an update with an ethernet cable and the card plugged in? Try that then check 'Additional Drivers'. See anything for the wireless? The D-Link doesn't use a D-Link wireless chipset. Could be anything in that one, but looks like fully supported as is working. Also, tell us what Ubuntu release you are using ...

---

### Post by DrNugget on 2012-12-18
J:lolflag:ust wanted to say first of all thanks so much for the quick help and tips for posting on the forums! 
Secondly, I entered sudo lshw -C network on the terminal, and strangely enough my connection was resolved and hasn't broken since! 
I'll go ahead and give you the result anyway, just in case any other people might find this info useful:
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: c8:60:00:de:bf:17
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff
  *-network
       description: Wireless interface
       product: AR5212/AR5213 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:03:05.0
       logical name: wlan0
       version: 01
       serial: 00:0f:3d:ac:62:ca
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.5.0-17-generic firmware=N/A latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:20 memory:febf0000-febfffff

I'm using Ubuntu 12.10, and other than this little problem, its workin' great!
thanks again!

---

### Post by steeldriver on 2012-12-18
Hi I used to have a couple of ath5k based devices - I'm a bit out of the loop with wireless issues but iirc the usual problem with them is the hardware encryption

If you are comfortable with doing things in the terminal you can try

```
sudo modprobe -rv ath5k
sudo modprobe -v ath5k nohwcrypt=Y
```It's not a permanent change so it can't hurt to try afaik - *if* it helps we can make it persistent via a config file

---

### Post by Bucky Ball on 2012-12-19
No probs with the help and tips. That's what these forums are all about ... ;)

> **DrNugget said:**
> ... I entered sudo lshw -C network on the terminal, and strangely enough my connection was resolved and hasn't broken since! 

Have you rebooted the computer and still working? If so, mark thread as 'Solved' from thread tools to help others. 

Your output from that last command looks fine. 

 ```
driver=ath5k driverversion=3.5.0-17-generic
```That card is supported by the kernel, no faffing about required (don't need to install drivers for it as they are already part of the Ubuntu install) so I don't doubt it should work through a restart.

Could you provide the output of this, just to verify:
```

iwconfig
```Cheers and glad to hear it's working to this point, though not sure what happened there! ...

---

