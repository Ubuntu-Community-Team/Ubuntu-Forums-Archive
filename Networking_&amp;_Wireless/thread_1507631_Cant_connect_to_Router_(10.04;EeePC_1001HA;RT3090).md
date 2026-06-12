---
title: "Cant connect to Router (10.04;EeePC 1001HA;RT3090)"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by mattt360 on 2010-06-11
Hey I'm new to Ubuntu. I just install Ubuntu 10.04 on my EeePC and I'm loving it. the only problem is I can only get wired internet.
I was going around the help but I couldn't find my problem. others also have had the same problem as me. here's all the information I think you'll need:
OS: Ubuntu Desktop 10.04
Model: EeePC 1001HA
Wireless Card: RT3090
Lshw Output:
           *-network DISABLED
                description: Wireless interface
                product: RT3090 Wireless 802.11n 1T/1R PCIe
                vendor: RaLink
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
                resources: irq:17 memory:fbff0000-fbffffff
Lsmod Output:
Module------------------Size--Used by
rt3090sta-------------674216--0
NOTE: I cut out alot of the outputs because the didn't appear useful (like my USB devices etc.)

NOTE2:any commands you want me to run just let me know (BTW I wont run stuff like mkfs... I'm not that new)

NOTE3:Ubuntu Desktop works quite well on a EeePC actually.
EDIT: vBulletin wont let me have multiple spaces! I'll replace them with dashed in the lsmod output.

---

### Post by BoneKracker on 2010-06-11
It looks to me like that driver is a problem right now.

You may find useful information in here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620)

This may also be useful information:
[http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/](http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/)

---

### Post by jackthechemist on 2010-06-11
Well I know that with windows you sometimes have to tell the computer which interface to use (NIC or wireless)  I'm running Ubuntu now and the eth0 interface i currently active, maybe you have to switch it to eth1? Just an idea...

---

### Post by katzelai on 2010-06-13
Try to upgrade the kernel to version 2.6.34. That was how I have my eee PC 1001PX wireless working.

---

### Post by rukiaEnix on 2010-06-13
download madwifi-hal and install it, it worked for me I also have an EEE PC.

here you will find all you need:   [http://madwifi.org/](http://madwifi.org/)

---

### Post by changlinn on 2010-07-10
Thanks katzelai, just got one of these, followed the guide here to upgrade the kernel and wifi works.
[http://usablesoftware.wordpress.com/2010/05/26/switch-to-a-newer-kernel-in-ubuntu-10-04/](http://usablesoftware.wordpress.com/2010/05/26/switch-to-a-newer-kernel-in-ubuntu-10-04/)

---

