---
title: "Intrepid 8.1 ndisgtk: &quot;Could not find a network configuration tool&quot;"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by femme_du_seul on 2009-02-18
Hello there,

I'm having the same problem as this user: [http://ubuntuforums.org/showthread.php?t=991374&page=2](http://ubuntuforums.org/showthread.php?t=991374&page=2)

I have tried the steps that worked for him but did not get the same results :( 

Here's some information on my system and what I've done so far:

Compaq Presario R3000 with broadcom BCM4306

I've tried:

[I]* removing ssb, b43, bcm43xx
* getting ndiswrapper, ndiswrapper-utils, ndisgtk , opening ndisgtk and getting it to use bcmwl5.inf[/I]

I've gotten the ndisgtk to load the driver but when I try to configure the network I get this error. Can somebody PLEAAAAASE help me, I would really really REALLY appreciate it :)

I've spent 3 days working on this already and I feel oh so close!

Thanks in advance!

---

### Post by superprash2003 on 2009-02-18
post output of the following
1)iwconfig
2)iwlist scanning

 hope you have rebooted!!

---

### Post by femme_du_seul on 2009-02-18
In addition to above, here's what I get with the:

**lshw -C network** command

```
WARNING: you should run this program as super-user.
    *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:05:3e:4e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
*-network:1             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb

  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:b6:bf:a7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5e:a4:38:bc:3b:9d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

---

### Post by femme_du_seul on 2009-02-18
> **superprash2003 said:**
> post output of the following
1)iwconfig
2)iwlist scanning

 hope you have rebooted!!

Hi Superprash, thanks so much for replying!! And yes I rebooted, but the little blue light still won't go on when I try to enable wireless.

As an aside: I download Ubuntu Intrepid 8.1 and the file had 'i386' in the download name, however my compaq presario is running AMD Athlon 64. I'm not sure if this would have any effect? I didn't see an AMD version of Ubuntu.

**iwconfig:**

```

lo     no wireless extensions.

eth0   no wireless extensions.

pan0   no wireless extensions.

```

**iwlist scanning:**

```

lo     Interface doesn't support scanning.

eth0   Interface doesn't support scanning.

pan0   Interface doesn't support scanning.

```

---

### Post by femme_du_seul on 2009-02-18
I also found a reference to this error in the bug defect database, but there seem to be no solutions posted.

[https://bugs.launchpad.net/ubuntu/+source/ndisgtk/+bug/295892](https://bugs.launchpad.net/ubuntu/+source/ndisgtk/+bug/295892)

---

### Post by superprash2003 on 2009-02-19
have you tried this [http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html](http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html) .. if this doesnt work try thi [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) ..

---

