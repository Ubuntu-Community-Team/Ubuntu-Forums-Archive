---
title: "Wireless can't see my network SSID"
date: 2011-11-02
forum: Networking &amp; Wireless
---

### Post by mrdavidberry on 2011-11-02
Hello,

Following the HOWTO:
The issue is that when I click on the network manager wedge icon, I get a list of available networks, none of which is the router on the other end of my desk.  Other devices (Windows PCs and Android Phones) are seeing my network fine.  I have tried "connect to a hidden network" but that doesn't work.

I've run through the instructions in the HOWTO post to this thread and typed all the outputs below.

If anyone can help, this would be greatly appreciated!

Thanks
D


Make and Model:
Compaq-mini-100c netbook

lspci:
01:00 Network Controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

lsusb: not a usb wireless stick so nothing useful.

iwconfig:
lo    no wireless extensions
eth0  no wireless extensions
eth1  IEEE 802.11 Access Point: Not-Associated  Link Quality:5 Signal level:0 Noise level:0 Rx invalid nwid:0 invalid crypt:0 invalid misc:0

ifconfig:
eth1   Link encap: Ethernet HWAddr 00:26:5e:06:23:86 inet6 addr:fe80::226:5eff:fe06:2386/64 Scope:Link  UP BROADCAST MULTICAST MTU:1500 Metric:1 RX Packets:0 errors:0 dropped:0 overruns:0 frame:0 TX packets:0 errosr:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000 RX bytes:0 (0.0B) TX bytes:0 (0.0 B) Interrupt:16 Base address:0xc000

lsmod |grep "eth1": nil and nothing that looks like it might be the right thing.

dmesg|grep "eth1":
[  22.001790] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.38
[  34.304081] eth1: no IPv6 routers present
[1089.024043] eth1: no IPv6 routers present

sudo lshw -C network:
*-network
    description: Wireless interface
    product: BCM4312 802.11b/g LP-PHY
    vendor: Broadcom Corporation
    physical id:0
    bus info: pci@0000:01:00.0
    logical name: eth1
    version: 01
    serial: 00:26:5e:06:23:86
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
    configuration: broadcast=yes driver:wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11b/g
    resources: irq: 16 memory:feafc000-feafffff

iwlist scan:
lo    Interface doesn't support scanning.
eth0  Interface doesn't support scanning.
eth1  Interface doesn't support scanning.

uname -mr:
3.0.0-12-generic i686

sudo /etc/init.d/networking restart:
* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
* Reconfiguring network interfaces... [OK]

---

### Post by mrdavidberry on 2011-11-05
Please help!

My wife uses this netbook when she's getting our baby to sleep and she's really missing it!

Thanks

---

### Post by Tiit_Helimut on 2011-11-09
*bump*

Same issue on Samsung N130 netbook... can see other networks but not mine! I'm currently connected to this network on a Windows machine so there shouldn't be a problem...

All was fine after installing Ubuntu 11.10 but after updating to the latest kernel, it stopped working...

A fix or any advice would be greatly appreciated!

---

### Post by Mr.Carramba on 2011-11-09
I have same issue on thinkpad x200. For me it works to restart network manager couple of times and it connects to my network.

---

### Post by RedSingularity on 2011-11-10
Well if you can see and connect to other access points then I dont think the issue is your computer.  Have you checked the router?  Maybe perform a factory reset.  Make sure its not operating on 802.11n 5GHz frequency instead of the 802.11g 2.4GHz range.  I am guessing your netbook is made for 802.11g networks.

---

### Post by dik23 on 2011-12-09
I had the same problem after updating from 10.10 > 11.10

Definatly not a problem with my routers / network since many other devices continued to work fine.

In the end this post worked for me and my Compaq-mini-100

[http://ubuntuforums.org/showpost.php?p=10050759&postcount=7](http://ubuntuforums.org/showpost.php?p=10050759&postcount=7)

Hope this helps

---

### Post by dik23 on 2011-12-10
Unfortunalty it seems this is necessary each time the kernel is updated.

Does anyone have a better fix ?

Quite why this needs a fix is beyond me. Pretty poor seeing how many of these wireless chips are out there.

---

