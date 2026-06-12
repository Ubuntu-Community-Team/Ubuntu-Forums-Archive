---
title: "ubuntu 9.10 and dell wireless"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by Yair87 on 2009-11-14
hello,
i'm a linux newbe, and i just installed ubuntu 9.10 on my dell 1535 studio laptop.
and now it seems i have no wireless.
i have no idea what to do.
please help me.
thanks

---

### Post by t0mppa on 2009-11-14
First to give us a bit more information to work on, open up terminal (Applications / Accessories / Terminal), run **lshw -C network** and post here with the results.

---

### Post by Yair87 on 2009-11-14
thanks for the quick answer.
here it is:

WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f6cfc000-f6cfffff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:7c:f5:08
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v2.09 ip=192.168.1.103 latency=0 multicast=yes
       resources: irq:30 memory:f69f0000-f69fffff

---

### Post by t0mppa on 2009-11-14
Ok, BCM4312 is easiest to get working with the Broadcom STA, which you should be able to find from the proprietary driver section (System / Administration / Hardware Drivers).

Currently the b43 driver is associated with it, but in order for that to work, you need to install the *b43-fwcutter* package and use it to "cut" the firmware, which is a proprietary piece of software copyrighted by Broadcom that can't be legally distributed by just anyone and thus not a part of Ubuntu installation by default. And to top that, there's one revision (PCI-code [14e4:4315], you can check yours with **lspci -vnn | grep 14e4**) of BCM4312 that isn't yet supported by the b43 at all.

---

### Post by Yair87 on 2009-11-14
there is currently nothing in my hardware drives.
and 4315 IS my pci code.
what does it mean? i can't use my wireless with ubuntu??

---

### Post by ublintu on 2009-11-14
Hi,
I have a Dell Vostro 1000 with BCM4328 802.11a/b/g/n
I don`t know it`s working 4 you or not, but this solved my problem, hopefully for you to (the first post) :
[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

---

### Post by Kyan123 on 2009-11-14
hello I am a newbie to Ubuntu, I have had Window vista previously, and i found out ubuntu is good to use.  After i downloaded the newest version, my wireless did not work. Here is the info i got:
buivannam@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:52:a3:d8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 multicast=yes
       resources: irq:30 memory:f68fc000-f68fffff ioport:de00(size=256)
buivannam@ubuntu:~$ 

PLZ HELP

---

### Post by paguilar on 2009-11-14
I just got past this hurdle minutes ago.  I have a Dell Latitude D830 and couldn't get wireless working after installing Karmic.

I've been pulling info from various forums and finally got it working.  I had to download and use WICD and enable SSID broadcast on my private network in order to get it to work.  The original network-manager just didn't work.

The downside is now, the Wi-Fi light won't stop blinking!  It's annoying but at least it's finally working.

Hope this helps.

---

### Post by ublintu on 2009-11-14
So the link what I posted and there the guide, it is not working for you? If not, just let me know and I will delete it from here.

---

### Post by t0mppa on 2009-11-14
> **Yair87 said:**
> there is currently nothing in my hardware drives.
and 4315 IS my pci code.
what does it mean? i can't use my wireless with ubuntu??

Ok, then you need to install the bcmwl-kernel-source package (one way is described in the post referred to by ublintu), as it contains the STA in Karmic.

And it just means you can't use the b43 driver that was assigned to your wireless. You should still be able to get a perfectly working wireless with the STA.

> **Kyan123 said:**
> hello I am a newbie to Ubuntu, I have had Window vista previously, and i found out ubuntu is good to use.  After i downloaded the newest version, my wireless did not work. Here is the info i got:
buivannam@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:f69fc000-f69fffff


Unclaimed means there's no driver associated for it. So, just follow the same advice as Yair87 to get the Broadcom STA driver installed.

> **paguilar said:**
> I had to download and use WICD and enable SSID broadcast on my private network in order to get it to work.

...

Hope this helps.

While switching to WICD can get you past some of the hiccups with Network Manager (and sometimes vice versa), it will not do any good to these two, before they have working drivers for their cards.

---

### Post by Yair87 on 2009-11-17
Thank You Guys!
It Worked.

---

