---
title: "Needing help with yet another broadcom adapter"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by Jh60082 on 2009-02-10
Hi there. I recently installed ubuntu on my laptop however I can not connect to wireless internet through my Broadcom adapter (I have no idea what model number it is) I tried the going into system > administration > hardware drivers and that whole message came up "No proprietary drivers are in use by this system" came up, but the entire box below it was blank, nothing was there. I tried the response on this post ([http://ubuntuforums.org/showthread.php?t=1065534](http://ubuntuforums.org/showthread.php?t=1065534)) However, i was unable to do that last command, it said it was not found.

And now i do not have any wireless configuration options at all. I am familiar with Linux but this wireless stuff is driving me up the wall, any help is greatly appreciated. Thank you!

---

### Post by Ayuthia on 2009-02-10
You might try the following instead:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo /etc/init.d/networking restart
```I left out the ing at the end of network in that post.

If it does not work, please post the results of:
```
lspci -nn
lshw -C network
```

---

### Post by Jh60082 on 2009-02-10
Well I redid the whole sudo modprobe thing and this was the output of that:
```

jeremiah@hmrq02:~$ sudo modprobe -r b43 ssb wl
[sudo] password for jeremiah: 
jeremiah@hmrq02:~$ sudo modprobe wl
jeremiah@hmrq02:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
jeremiah@hmrq02:~$ 
```

Here is the output of lspci -nn 
```
 
jeremiah@hmrq02:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
02:07.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev a9)
02:07.1 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev a9)
02:07.2 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 01)
02:08.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03) 
```

Here is lshw -C network ```
jeremiah@hmrq02:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 10
       serial: 00:03:25:29:00:d2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.104 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       version: 03
       width: 32 bits
       clock: 33MHz
       configuration: latency=32
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ae:18:5a:d5:cf:c5
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by Ayuthia on 2009-02-10
You have a 4306 rev 03 card.  You should be able to use the b43 module.  If you have a working connection, you can install b43-fwcutter.

If you don't, you can try this guide:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

### Post by johnrw on 2009-02-12
> **Ayuthia said:**
> You have a 4306 rev 03 card.  You should be able to use the b43 module.  If you have a working connection, you can install b43-fwcutter.

If you don't, you can try this guide:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

I have a very similar problem I was going to post about except that it's a 4306 rev 02 I'll go away and follow your guide first, if no go expect long screed!

---

### Post by Jh60082 on 2009-02-19
Solved! Not sure how but I guess when I had my laptop connected to the Internet through the Ethernet it downloaded the necessary information to activate hardware drivers and I was successfully able to turn on my wireless. Thank you to everyone who helped!! I appreciated it so much!! Forums are waaayyy better than tech support lines :D

---

