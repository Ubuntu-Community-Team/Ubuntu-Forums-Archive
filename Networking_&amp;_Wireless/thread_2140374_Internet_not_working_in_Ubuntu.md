---
title: "Internet not working in Ubuntu"
date: 2013-04-29
forum: Networking &amp; Wireless
---

### Post by p3thead on 2013-04-29
Hello there I'm not really sure if I should put this topic under "Network & wireless" or under the "Beginner" section since I'm not that experienced with Ubuntu I'll just put in under the Beginner section.

So on to my problem then, I had a version of Ubuntu (12.04) installed on my desktop computer alongside with windows 7 before and I had it like that for quite some time and it worked just fine. Then for some reason I just didn't bother booting my Ubuntu partition for quite some time and when I finally did a few weeks ago I just couldn't get a internet connection (I'm using a cable). So I just figured that it might be the drivers for the network card not working properly or something like that. 

So I just wiped out my Ubuntu partition and reinstalled the new release (13.04) and it's still the same problem. 

It just won't register the network connection for some weird reason, I tried to reinstall it multiple times and even tried running it directly from the USB but yea, same problem, won't register a working internet connection.

Another weird thing is that when I've booted Ubuntu and just gonna reboot and go onto my Windows partition again, the internet connection just won't register in windows just like it won't in Ubuntu. It's just saying that I need to plug in a ethernet cable (which is already plugged in ofc).

The only way to get the internet to work properly again is to keep my computer shut off for a few minutes before booting up again and then it works like a charm.

I plugged in another ethernet card as well just to see if it were something wrong with the one integrated on my motherboard(GA-870A-UD3) and it didn't really solve anything...

Anyone got any idea of what might be wrong?

---

### Post by Bucky Ball on 2013-04-29
*Thread moved to **Networking & Wireless**.*

Open a terminal, paste this in and post the results back here, please (with just one wireless card in, perhaps the original which was working in 12.04 LTS before):

```
sudo lshw -C network
```

Just wondering, was the wireless on the Windows side getting dodgy prior to booting Ubuntu after some time? When you put in the other card, did it have the same issue as the original in both Ubuntu and Win? Are there other devices running wirelessly on the same router in the same LAN and they're not having this problem?

---

### Post by p3thead on 2013-04-29
I'm not even using wireless, It's just getting dodgy AFTER I've booted Ubuntu. 

Will test the command once I get home..

Just my desktop on my router.

And yes it's the same issue with the other card. :(

---

### Post by Resistent on 2013-04-29
Check the cable ! Maybe you have a contact error between PC and router.
Why else would it say "[COLOR=#000000]plug in a ethernet cable"..

Also reboot the router ! I had such problems too. 

Also, they could deactivate your internet connection on the other side for updating the cable router...
Then it will not work for some minutes..





[/COLOR]

---

### Post by p3thead on 2013-04-29
-network               
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 03
       serial: 1c:6f:65:89:3a:88
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:48 ioport:ae00(size=256) memory:fdaff000-fdafffff memory:fdaf8000-fdafbfff memory:fda00000-fda1ffff


There you go, sorry for the late response though but just got back home..


> **Resistent said:**
> Check the cable ! Maybe you have a contact error between PC and router.
Why else would it say "[COLOR=#000000]plug in a ethernet cable"..

Also reboot the router ! I had such problems too. 

Also, they could deactivate your internet connection on the other side for updating the cable router...
Then it will not work for some minutes..

[/COLOR]

I'm pretty damn certain that it has nothing to do with what you described.. The card just stops working everytime I try to run Ubuntu and by booting Ubuntu I create the same problem for windows if I do not let the computer stay off for a couple of minutes before booting windows. I just haven't bothered with it before, until today when I tried to reinstall Ubuntu because I thought it would fix it..

---

