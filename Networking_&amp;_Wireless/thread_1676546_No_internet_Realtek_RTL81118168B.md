---
title: "No internet Realtek RTL8111/8168B"
date: 2011-01-27
forum: Networking &amp; Wireless
---

### Post by gorojoe on 2011-01-27
Hello

I am fresh off the Microsoft boat. I've wanted to try Linux for a while, and finally tried it out. I have Ubuntu 10.10 installed on an older laptop and have been enjoying it for a while. My problem arose when installing on my main desktop. I have a duel boot with windows 7.

I have no internet. I have looked over a number of forums and nothing seems to apply to me. There seems to be an old issue where Ubuntu would use the wrong module for my network card, but that looks like it has been fix in 8.04. Btw i have an on-board network adapter, with a wired connection. 

I have tried a couple of things:
[B]
sudo dhclient eth0[/B]

Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

SIOCSIFADDR: No such device
ech0: ERROR while getting interface flags: No such device
ech0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device



**ihconfig**

eth0      Link encap:Ethernet  HWaddr 1c:6f:65:20:cc:10  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:49 Base address:0xe000 

eth0:avahi Link encap:Ethernet  HWaddr 1c:6f:65:20:cc:10  
          inet addr:169.254.6.26  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:49 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

**Lspci-v**
I skipped most of it, but here is what's under the network controller

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 49
    I/O ports at ce00 [size=256]
    Memory at fbbff000 (64-bit, prefetchable) [size=4K]
    Memory at fbbf8000 (64-bit, prefetchable) [size=16K]
    [virtual] Expansion ROM at fbb00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

Can anyone help? Thanks in advance

---

### Post by chili555 on 2011-01-27
First, it looks like you made a typo:> SIOCSIFADDR: No such device
[COLOR="Red"]ech0[/COLOR]: ERROR while getting interface flags: No such device
ech0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Is the result the same with:```
sudo dhclient [COLOR="Red"]eth0[/COLOR]
```Network Manager will probably interfere, but we can get some clues from the result.

When you run:```
sudo lshw -C network
```Does it say link=yes or link=no. The system will not connect if it *thinks* there is no link. In that case, see:  [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

### Post by gorojoe on 2011-01-27
> **chili555 said:**
> First, it looks like you made a typo:Is the result the same with:[CODE]sudo dhclient [COLOR=Red]eth0[/COLOR]
[COLOR=Red]
[COLOR=Black]As far as i can tell, that is the same. Just making sure, its eth[zero]. It might look like a O because it was in bold. Anyways, just to make sure i copied and pasted your command and it does the same thing. [/COLOR][/COLOR]Actually, I tried both 0 and O and it does the same thing, weird.  

Oh yes thank you. Link=no, and i followed your link. This was the problem. I'm running updates in Ubuntu and will change the setting in windows as soon as it finishes. 

Thank you so much

---

### Post by gorojoe on 2011-01-27
How do i mark this thread as solved?

---

### Post by chili555 on 2011-01-27
At the top, select Thread Tools, drop down and select Mark Solved.

---

