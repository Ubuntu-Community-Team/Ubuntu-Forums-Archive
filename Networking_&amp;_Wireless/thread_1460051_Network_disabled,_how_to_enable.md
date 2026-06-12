---
title: "Network disabled, how to enable?"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by mikehpro on 2010-04-22
Hello There!

I just installed Ubuntu 9.10. I got a problem with my wireless card. I did everything that was on the official Ubuntu site to try to solve the problem. But it didn't work. The thing is, when is use the lshw comment it says my card is disabled. Ubuntu site says that there is a switch or something on your laptop. But i don't got any switches or something for the network card. I don't know how to enable it and i need to cause i have only wireless internet in my house. And it is a notebook so i want to use wireless. Please help me!

Here is what lshw says:
   [FONT=&quot]  *-network:0 DISABLED    
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 6
       bus info: [EMAIL="pci@0000:00:06.0"]pci@0000:00:06.0[/EMAIL]
       logical name: wmaster0
       version: 01
       serial: 00:10:60:63:47:54
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci latency=64 multicast=yes wireless=IEEE 802.11bg
       resources: irq:0 memory:ffffe000-ffffffff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: [EMAIL="pci@0000:00:12.0"]pci@0000:00:12.0[/EMAIL]
       logical name: eth0
       version: 74
       serial: 00:40:d0:86:dd:30
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=128 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:11 ioport:e200(size=256) memory:d0000000-d00000ff[/FONT]

---

### Post by chili555 on 2010-04-22
> But i don't got any switches or something for the network card.I have never seen a notebook with no switch or key combination to enable and disable wireless. What is the make and model of yours? May we see:```
dmesg | grep -e rt2 -e wlan
lsmod | grep rt2
```Thanks.

---

### Post by mikehpro on 2010-04-22
> **chili555 said:**
> I have never seen a notebook with no switch or key combination to enable and disable wireless. What is the make and model of yours? May we see:```
dmesg | grep -e rt2 -e wlan
lsmod | grep rt2
```Thanks.

Thanks for you help! There is a key combination, which doesn't work. It is FN + F1 but that one doesn't work for me! What now?

---

### Post by chili555 on 2010-04-22
How about the answers to my questions?> What is the make and model of yours? May we see:
```
dmesg | grep -e rt2 -e wlan
lsmod | grep rt2

```
Thanks.

---

### Post by compdoc on 2011-05-10
I moved my new Ubuntu 11.04 system to a different motherboard which had different network cards, and 'sudo lshw -C network' showed '*-network disabled' for both interfaces. Also, my entries for /etc/network/interfaces were being ignored and 'sudo ifconfig' was showing the wrong information.

After much searching, I found the answer and I wanted to post it here so that next time I have to solve this problem, I'll find it faster.

Edit the file /etc/udev/rules.d/70-persistent-net.rules and delete all entries for the network cards you find. These entries will be recreated correctly when you reboot the PC, and your network will then be using the settings in /etc/network/interfaces.

---

