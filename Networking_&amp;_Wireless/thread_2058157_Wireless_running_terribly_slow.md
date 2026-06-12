---
title: "Wireless running terribly slow"
date: 2012-09-15
forum: Networking &amp; Wireless
---

### Post by ImTheBushMaori on 2012-09-15
Hello everyone.

I have been having a problem with my Ubuntu ever since I decided to install it onto my laptop which was around about 6 months ago and only now decided to speak up about my problem because it seems to be a pretty big one.

I love this OS compared to Windows and Mac but there is much for me to learn on this before I get down to the real stuff but first off I would like to exclaim my wireless problem.

My wireless seems to be very picky on which routers it likes, for example, my HG556A which is made by Huawei runs perfect for my desktop, which is running XP and other devices such as iPods and mobiles, but when it comes to my laptop running 12.04 Ubuntu it doesn't like it very much. It decides to only run at about 0.20 mb/s and my desktop runs at 15.01 mb/s.

Now my laptop likes running on a Thomson 0BBB5C (which I used at a mates house) and decides to run perfectly fine on that so what im really asking is if there is any chance there is a fix out there or will I have to go out and buy a new router?

Thank you for your time.

---

### Post by Bucky Ball on 2012-09-15
*Thread moved to **Networking & Wireless***

[CENTER] *
[/CENTER]
 
Welcome and glad you mentioned it! Hopefully you can get some help. Could you open a terminal (Applications>Accessories>Terminal) and paste in these two commands, input one at a time:

```
sudo lshw -C network
```... and:

```
iwconfig
```Copy their outputs  and paste back here, please (control+shift+c or v for copy/paste in terminal). That will show the wireless card, what driver is currently loaded and the status of your connection.

Could you also have a look in 'Additional Drivers' and see if there is anything there for your wireless. ;)

This is sounding like it might be a simple setting either on the router or your local machine in Network Manager, but let's see what the current situation is.

Are you using static (set on the local machine) or automatic (served by the router) IP addresses or don't know?

---

### Post by ImTheBushMaori on 2012-09-15
Hi Bucky.
This is all that came up.

  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:5f:c4:c1:ca
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-29-generic firmware=N/A ip=192.168.1.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:91200000-9120ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: 00:23:8b:ef:f9:f8
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:2000(size=256) memory:91004000-91004fff memory:91000000-91003fff memory:91010000-9101ffff

Now as you can probably see already I can only read about a quarter of that and I have updated everything I can (well, what I think I can haha) so yeah.
Thanks.

---

### Post by ImTheBushMaori on 2012-09-15
By the way thanks for moving my thread to here. 
I really had no idea where to put so beginners sounded good to me haha

---

### Post by Bucky Ball on 2012-09-15
Cool. The correct drivers appear to be installed for that card. Result of:

```
iwconfig
```... please. 

These Atheros models have worked pretty much out-of-the-box for ages so thinking perhaps it's a setting. That command will tell us more.

You might also like to try the suggestions in posts #5 &#9 here:

[http://ubuntuforums.org/showthread.php?t=894177](http://ubuntuforums.org/showthread.php?t=894177)

---

### Post by ImTheBushMaori on 2012-09-16
Hey Bucky

Thanks for your help but I seemed to have found a fix for it now.
I just had to change my bit rate to this:

sudo iwconfig wlan0 rate 54M

That seems to fix it so thanks anyway!

EDIT: Just saw that it was one of the answers you considered so thanks a heap mate!

---

### Post by Bucky Ball on 2012-09-16
No probs. Glad that it's fixed. Please mark thread as 'solved' from Thread Tools. Enjoy! ;)

---

