---
title: "need help finding a usb wireless network adapter that can inject packages"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by djmh on 2009-07-19
i have looked around on the Internet, for a wireless adapter that is capable of injecting packages.
i know they cant be that rare, but i cant seem to find any.
if anyone know what terms i should be looking for ...because i believe that searching "wireless adapter capable of injecting packages" is what is throwing off my whole search.

i need it because i plan to do some security testing, and just want to try out bt3 on my home network. and test how vulnerable my dads shop would be .

so if you could give me a link, a search term, even what it would say on the back of the wireless adapter box, or anything to point me in the right direction to getting one that would be great.

by the way, it needs to be usb .... thanks evryone :) !

the dell mini 9 dose not come able to inject packages stock does it ??
it has wireless 802.11G mini card.

thanks ...

---

### Post by pytheas22 on 2009-07-19
Whether a card will support injection depends on its chipset.  Unfortunately, it's usually not easy to know which chipset is in a particular wireless card until you plug it into your computer and use the 'lspci' command to look it up.  But if you search Google by the name of the chipset you're looking for rather than just using keywords like "injection," you'll probably have better luck.

The aircrack people have a [list of chipsets]("http://www.aircrack-ng.org/doku.php?id=compatibility_drivers") that should support injection.  If it says supported by aireplay, it means injection will work.  Many of the chipset families listed there aren't available in USB sticks, but I know that the Ralink rt2570 and rt73, at least, do come in USB devices and work great with injection.

You can also try searching through comments on the web pages of wireless adapters to see if anyone mentions injection or aircrack.

Also, I'm not positive but I thought the Dell 9 Mini came with a Broadcom-based wireless card.  If so, injection should probably work using the b43 driver (although there are a few Broadcom chips that don't support b43).  If you post the output of these commands, I should be able to tell you with more certainty whether you can inject using the Mini's card:
```

lspci -nn
lshw -C Network
```

Injection support on the b43 driver is relatively new, so it could just be the case that Backtrack's drivers are too old to support it, but if you compile a more recent version of b43 from source, it would work.

---

### Post by djmh on 2009-07-20
ok, your post seems to be just what i needed.
though it leaves me with a few more questions.

[http://www.bestbuy.com/site/olspage.jsp?skuId=7012485&st=belkin+wirelessw+G+network+adapter&lp=1&type=product&cp=1&id=1099392876384](http://www.bestbuy.com/site/olspage.jsp?skuId=7012485&st=belkin+wirelessw+G+network+adapter&lp=1&type=product&cp=1&id=1099392876384)

can i purchase that one and inject packages ?

beacause as far as i can tell from my researching, its not so much the adapter ..as it is the driver on the adapter 

so when ever i searched for Ralink rt2570 i found a bunch of sites talking about the previously mentioned adapter .

[http://opensource.bureau-cornavin.com/belkin/index.html](http://opensource.bureau-cornavin.com/belkin/index.html)

so what i gather is that i need to install the correct drivers or chipsets....how difficult is this going to be to have setup and working ?

ideally i want to be able to test systems (a few people want me to test theirs also now) but, i want to plug in the adapter, test the system, then unplug the adapter and use my internal network card.

am i going to be up against a difficult task ?

as for the codes ...

richy@richy-netbook:/$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 System peripheral [0880]: JMicron Technologies, Inc. SD/MMC Host Controller [197b:2382]
02:00.2 SD Host controller [0805]: JMicron Technologies, Inc. Standard SD Host Controller [197b:2381]
02:00.3 System peripheral [0880]: JMicron Technologies, Inc. MS Host Controller [197b:2383]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

richy@richy-netbook:/$ sudo lshw -C Network
[sudo] password for richy: 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:23:08:47:03:bd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.1.101 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:d4:56:16
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 0a:d2:42:2f:aa:a5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
richy@richy-netbook:/$ 

it would be best if my mini could inject all on its own...but i had searched to see if it could before and i was unable to find any results, maybe you can shed some light on this :)

so theres the output of those two codes, i appreciate any help.
thanks !

---

### Post by pytheas22 on 2009-07-20
> ok, your post seems to be just what i needed.
though it leaves me with a few more questions.

[http://www.bestbuy.com/site/olspage....=1099392876384](http://www.bestbuy.com/site/olspage....=1099392876384)

can i purchase that one and inject packages ?

Maybe.  The problem is that, according to the second link you posted, devices sold under the name "Belkin Wireless G" could contain several different chipsets.  This is why it's so hard to find a wireless card that works with aircrack; the manufacturers tend to change the chipsets in the devices while continuing to sell them under the same exact name, and there's usually no way to know which chipset is in the device until you can plug it into your computer.

You could try buying that adapter and hope you get one of the versions with the Ralink chipset, but the other versions may not work with injection.

In some cases, the box or webpage for an adapter will mention a revision number, like "rev A" or "rev 2."  If you can find that information, you can usually look up which chipset is in the device.  But there's no guarantee that the revision number will be mentioned.

Your best bet may be to buy from a place where you can return the device easily if it turns out not to have a good chipset.

> 
so what i gather is that i need to install the correct drivers or chipsets....how difficult is this going to be to have setup and working ?

ideally i want to be able to test systems (a few people want me to test theirs also now) but, i want to plug in the adapter, test the system, then unplug the adapter and use my internal network card.

am i going to be up against a difficult task ?

Once you get a chipset that supports injection, getting the right drivers should not be difficult.  Under Ubuntu 9.04, most of the drivers will support injection out-of-the-box.  I don't know about Backtrack but I would imagine the situation would be similar there.  In any case, it's usually not very difficult to patch a driver for injection if necessary; there are instructions on the aircrack website with commands you can copy and paste.
> 
it would be best if my mini could inject all on its own...but i had searched to see if it could before and i was unable to find any results, maybe you can shed some light on this 

It looks like your internal wireless card has a Broadcom 4312 chipset, which is supposed to be supported by the b43 driver; however, you're currently using a different driver.  You can try switching to the b43 driver in Ubuntu by typing:

```
sudo rmmod wl
sudo rmmod b43
sudo modprobe b43

```

Then try starting the wireless card for injection by typing:
```

sudo airmon-ng start wlan0
```

(If you get a "command-not-found" error, you need to install the aircrack suite with "sudo apt-get install aircrack-ng.")

If you don't receive any error messages when running the last command, then injection should probably work on the internal device.  However, note that if you reboot, your system will default back to the other driver, so you will need to run those commands again to switch to the driver that supports injection.

---

### Post by djmh on 2009-07-20
ok, i will try thta after work tommorow ...just wanted to say thanks for your help - and really it resetting to teh default would be great, definatly preferable - so lets hope i can just use that .... if not i will just purchase one that i can return easily.

thank you so much for your help though.

---

### Post by djmh on 2009-07-20
your first command shut my wireless off ...i rebooted and got it back
and the second command give me this

richy@richy-netbook:/$ sudo rmmod b43
[sudo] password for richy: 
ERROR: Module b43 does not exist in /proc/modules
richy@richy-netbook:/$

the third did nothing ...

dose this mean i cant inject with my mini 9 ?

---

### Post by pytheas22 on 2009-07-20
Sorry, I should have explained those commands better.

The first command removes the wireless driver (named wl) you are currently using.  So yes, it will break the wireless.

The error message you received for the second driver is not serious; you can ignore it.

The third command inserts the new wireless driver (named b43).  If all goes well and b43 is able to bring up your device, your wireless should start working again at this point.

To tell whether b43 has brought up your wireless card successfully, check the output after the third command of *iwconfig*.  If there are any wireless interfaces listed, then b43 has brought up your device and you should be able to use it to inject.

Any changes made by these commands will be erased when you reboot, so if you encounter problems, just restart and things will be back to normal.

---

### Post by djmh on 2009-07-21
richy@richy-netbook:/$ sudo rmmod wl
[sudo] password for richy: (at this point wireless turns off)
richy@richy-netbook:/$ sudo rmmod b43
ERROR: Module b43 does not exist in /proc/modules (receive this error and no wireless still)
richy@richy-netbook:/$ sudo modprobe b43
richy@richy-netbook:/$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

richy@richy-netbook:/$

---

### Post by djmh on 2009-07-21
it seems it cant be done ...

[http://ubuntuforums.org/showthread.php?t=1150699](http://ubuntuforums.org/showthread.php?t=1150699)

but i may be able to get it working through a wireless adapter....

i really appreciate you taking your time to help me though pytheas.

---

### Post by djmh on 2009-07-21
if only there was any easier way to tell what chipset a adapter had ...
but, when i do purchase an adapter what will i need to do to see what chipset it has ? - radio shack in my town might actually let me test drive their adapter before purchase ..idk

---

### Post by djmh on 2009-07-21
[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)

wow...well if anyone else ever stumbles across this that link is the way to go ...

---

### Post by djmh on 2009-07-21
just one more question ....
i found one that should work

d liink WUA-1340 
it has the ra link chipset ....
but my question is - could this model have changed its chipset like you said the other one could have ? - or was that a brand that could have changed chipsets ?

what im asking is will this model still have the ra link chipset no matter what ?


also ...im looking at all these adapters speed ...G, N, others .... what one should i buy for best overall performance on several varying networks ?

---

### Post by pytheas22 on 2009-07-21
Yes, I guess b43 doesn't support your card.  [Their website]("http://linuxwireless.org/en/users/Drivers/b43#supported_chip_types") says it supports most 4312 cards, but maybe your model is an exception.

A quick Google search suggests that all versions of the D Link WUA-1340 are based on the Ralink rt73 chipset, which should be able to inject well (I have one myself), so you should probably be safe.  But the only to be totally sure is to plug the device into a Linux computer and type:
```

lsusb
```

The output will describe all USB devices attached to your computer, including the wireless card, and should mention the wireless chipset.

If you can convince Radioshack to let you plug the device in before buying, that would be the best way to go.

As for G vs. N mode, N is the newest standard and provides the highest speed and greatest range, but G works fine too.  If you get an N adapter for a decent price, go with that, but it's not going to make an overwhelming difference, so don't worry if you can only find a G device.

Also, be careful with Ralink devices that support N mode because I think (but could be wrong) that they all use newer chipsets and I'm not sure what the status of their Linux drivers is...they may be able to inject but I'm not sure.  The Ralink rt73 and rt2570 chips, which have been around for years, definitely support injection.

---

