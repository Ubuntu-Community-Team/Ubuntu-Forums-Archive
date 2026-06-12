---
title: "Ubuntu 9.10 - Dell Inspirion 6400 - wireless not working"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by raj_tech23 on 2010-03-14
Hi All,

I have formatted my windows-XP laptop(Dell Inspiron 6400) and installed Ubuntu 9.10 today.
I was happy to see Ubuntu screens until the time when I figured out my wireless light is not switching on. I tried pressing Fn+F2 several times but still the light doesn't come up. I spent like 3-4 hours in ubuntu forums but no where I got solution to my problem.

I am brand new to Ubuntu, so trying to figure out stuff.

Here is the o/p of what might be helpful :

raj@raj-laptop:~$ sudo lshw -C network
[sudo] password for raj: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:60:e8:bf
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.15.5 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:17 memory:ef9fe000-ef9fffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:92:bf:1e:6b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
raj@raj-laptop:~$ 

PLEASE HELP ME IF SOME ONE GOT SIMILAR ISSUE USING DELL INSPIRON 6400 A ND FIGURED OUT SOME SOLUTION.

Thanks in advance,
Raj.

---

### Post by bcbc on 2010-03-14
I've got a 6400 but it has an intel wireless card that worked out of the box. Anyway - here's a howto I found for your card - it's been around a while, but it should be a good start.
[http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568)

---

### Post by raj_tech23 on 2010-03-14
Hi bcbc,

Thanks for the response.
Out of the blue today I went into the System > Admin > Hardware Drivers and I found my wireless driver(Broadcom B43 Wireless Driver) in the list and I clicked on Activate button and it installed. After that I tried Fn+F2...tadaaa....It worked !!! So I am all happy in the morning and my laptop updated automatically to the day light saving on its own through wireless.

~Raj

---

### Post by bcbc on 2010-03-14
Well that was easy :)

Maybe you should post a comment on that thread so they can update the Howto. And mark this as solved.

Enjoy.

---

