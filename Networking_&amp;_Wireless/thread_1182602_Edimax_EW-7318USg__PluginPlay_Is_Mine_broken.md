---
title: "Edimax EW-7318USg | PluginPlay? Is Mine broken?"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by linorics on 2009-06-09
Update: Thanks for all the help guys. I posted a thread on how exactly I got it working here 
[http://ubuntuforums.org/showthread.php?p=7755396#post7755396](http://ubuntuforums.org/showthread.php?p=7755396#post7755396)


Ive been trying to install my "Edimax EW-7318USg" I just got from newegg. People say its plug and play but I've got no response. I've tried 8.04, 8.10, and 9.40 trying to get it to work. I've build the latest rt73 drivers, on all three but all a get is;

```

pan0      Link encap:Ethernet  HWaddr b6:d5:36:41:a3:dc  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

when I do iwconfig I get; 

```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

One thing that seems off to me is when the the device is inserted and I do lsusb I get;

```

[COLOR="Red"]Bus 008 Device 002: ID 7392:7318 [/COLOR] 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 413c:2105 Dell Computer Corp. 
Bus 002 Device 004: ID 0461:4d15 Primax Electronics, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Does anyone who has this card get any of this? 

The sticker on the back reads

```
EW7318USG93CE00122
```

Also the card seems to work fine on XP. 

Does any of this seem odd or abnormal? 

Any Ideas?

---

### Post by linorics on 2009-06-09
Also this is the output of my dmesg 

```
[46127.520016] usb 8-4: new high speed USB device using ehci_hcd and address 3
[46127.791601] usb 8-4: configuration #1 chosen from 1 choice
```

---

### Post by lindsay7 on 2009-06-09
lsusb output of a working Edimax EW-7318USG, purchased from Newegg three months ago. EW7318USG89CE04898

:~$ lsusb
Bus 002 Device 003: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13fe:2240 Kingston Technology Company Inc.
Bus 001 Device 003: ID 19ff:0102 Best Buy
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 03f0:0104 Hewlett-Packard DeskJet 880c/970c
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by nrvale0 on 2009-06-10
This looks identical to the behavior that I'm seeing from a device purchased from NewEgg about 2 weeks ago.

---

### Post by lindsay7 on 2009-06-10
Do you mean working or not working?

---

### Post by mattscar on 2009-06-22
My system can recognize some EW-7318USg adapters but not others. When I plug my customer's adapter into my Dell Inspiron 1501 running Ubuntu 9.04, lsusb gives me:

Bus 001 Device 012: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter

That's the right answer. But I just bought THREE adapters from NewEgg, and when I plug them in, I get:

Bus 001 Device 013: ID 7392:7318
Bus 001 Device 015: ID 7392:7318
Bus 001 Device 008: ID 7392:7318

These three aren't recognized as wireless adapters. There are no new wireless interfaces created.

Strange point. The adapter that can be recognized has its MAC sticker on the rear. The adapters that can't be recognized have their MAC stickers on the side. Hmm...

---

### Post by linorics on 2009-06-23
I recently email Edimax to ask them if the chipset or anything has changed. 

> Hello I just got you Edimax EW-7318USg off of newegg.com because of
its linux support. However none of the drivers that are supplied work.
People that have bought the same card, about 3 months ago, use the
same OS and are not having any problems getting it to work. Although
other people are having the same issue. Has the chipset in the Edimax
EW-7318USg been changed? Do I have a bad card? Is there a way to check
the card? Is there differant drivers than the rt73 for this card?
Please look at the following links to see the differences in the
working card and the non-working.

Mine --> [http://ubuntuforums.org/showthread.php?p=7429693#post7429693](http://ubuntuforums.org/showthread.php?p=7429693#post7429693)

Other --> [http://ubuntuforums.org/showthread.php?p=7429655&posted=1#post7429655](http://ubuntuforums.org/showthread.php?p=7429655&posted=1#post7429655)

Looking forward to hear from you,

There Replay:
> Hi,

Please read the attached guide for how to install the Linux driver.
To check whether this card is faulty or not, the quickest way is the install this card in the Windows PC using the driver of the product CD.

Thank you.

 

- Longcent

The attached PDF was a little outdated but I followed there guide on a fresh install of 8.04 hardy to no avail. 

I have since then sent it to newegg.com for a replacement. I'm going to email them with the info you have given. I let you all know what they say.

---

### Post by poorbadger on 2009-06-29
Just received one from Newegg today.
Same thing over here under 9.04.

```
~$ lsusb
Bus 002 Device 005: ID 7392:7318
```

and the following from dmesg

```
[12679.984130] usb 2-2: new high speed USB device using ehci_hcd and address 5
[12680.256445] usb 2-2: configuration #1 chosen from 1 choice
```

The sticker on the back of mine (Serial Number?) reads:

EW7318USG93CE00071

I'm going to make a 9.04 LiveCD and try it on another machine.

I thought I had read it worked out of the box under BackTrack 4 which is, in part, why I decided to pick one up.  But if there are indeed multiple chipsets who knows.  I just found a post on the BT forum w/ another member not able to get his card working.

I'll give both of those LiveCDs a try and see if either work out of the box and report back if I have any luck.  Might have to send it back and pick up an Alfa.

---

### Post by tuckie on 2009-06-29
See my post here: [http://ubuntuforums.org/showpost.php?p=7524721&postcount=7](http://ubuntuforums.org/showpost.php?p=7524721&postcount=7) for the "basic" principle behind getting this new card working.

---

### Post by ugm6hr on 2009-08-01
[http://ubuntuforums.org/showthread.php?p=7716964#post7716964](http://ubuntuforums.org/showthread.php?p=7716964#post7716964)

---

### Post by linorics on 2009-08-08
> **tuckie said:**
> See my post here: [http://ubuntuforums.org/showpost.php?p=7524721&postcount=7](http://ubuntuforums.org/showpost.php?p=7524721&postcount=7) for the "basic" principle behind getting this new card working.

Okay I did this and it worked flawlessly. Only problem is the drivers you suggested have issues with Kismet. But the idea is right on.

---

### Post by linorics on 2009-08-08
Thanks for all the help guys. I posted a thread on how exactly I got it working here [http://ubuntuforums.org/showthread.php?p=7755396#post7755396](http://ubuntuforums.org/showthread.php?p=7755396#post7755396)

---

