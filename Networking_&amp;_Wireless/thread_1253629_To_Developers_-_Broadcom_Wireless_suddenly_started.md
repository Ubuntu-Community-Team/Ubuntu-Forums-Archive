---
title: "To Developers - Broadcom Wireless suddenly started working..."
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by NunoANPereira on 2009-08-30
Hi there,

As everybody else that has a broadcom wireless card that is currently not supported by the 43XX drivers card I too didn't have mine working properly. I could see the wireless option in the network manager but dimmed and no wireless networks were detected/shown.

I Tried to figure it out for a while and soon discovered that drivers were being written. I realized then that would be a matter of time until my card in particular start being supported. Needless to say that as a wired connection didn't bother me at all I didn't even try anything to get it working.

Well today I happen to accidentally click the network manager icon at the tray and I was surprised to realize that **everyhing was working out of the blue..**. I was even more surprised when I checked the 43xx drivers website and the driver for my card is under development therefore not yet supported.

Knowing that I didn't try anything whatsoever to get it to work I am completely puzzled by this. The last Ubuntu update on my system was done around 3/4 days ago and I don't recall anything related to this being updated.

If any or some of the developers find this just as intriguing please let me know some other terminal outputs to help trying figure this out so we might help others.


Cheers,

Nuno

Hardware and Software settings:

Dell Inspiron 1545 Laptop - Intel T4200, Intel G45 - X4500HD, 4GB RAM


**Broadcom Details from  *lspci -vnn | grep 14e4***

```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
```**PCI detalis from *lspci***

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

---

### Post by t0mppa on 2009-08-30
Not a developer, but some things that caught my eye:

Did you ever bother trying the Broadcom STA driver that they released some months ago? It supports the newer chips (yours included) and since it came out, the only trouble child in the Broadcom chip family is really the 4318.

Also, you'd probably want to run **lshw -C network** from terminal to find out which driver it is that is working for you now.

---

### Post by nunopereira on 2009-08-30
No I didn't try that. I read that they are known to have bugs, might not be true, but as a wired connection didn't bother me I decided not to try anything.

The strange bottom line of the story is that from a fresh system install, after 3 weeks of not working properly, something that a lot of users are striving to get working, started running smoothly without intervention (at least intentional) to do so.

If this is from an update it's explained. Still I really don't recall updating anything related to this.

Nevertheless here's the output for **lshw -C network**

```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:d7:4b:19
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.2.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:47:b2:0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8a:aa:13:b9:7d:3e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```


Cheers,

Nuno

---

### Post by t0mppa on 2009-08-31
> **nunopereira said:**
> configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=192.168.2.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11

Well, wl is the module name for the STA, so I guess you're using it now. You said the wireless just suddenly started working, so does that mean you've tried to use it daily or it just finally automatically connected to a network for the first time a few days ago?

---

### Post by nunopereira on 2009-09-01
No I haven't tried to use it in any way. 

The wireless option in the network manager was dimmed and the wireless networks were not even detected. The card itself was obviously detected but it was not working. There was no way even if I wanted to at the time to connect or try to connect to any wireless network. The only option available to me was the Wired Network. For a few weeks after system updates I would just click on the icon of the network manager just to check if anything had changed but because it kept like that for a long time I gave up on checking after each update.

But a couple of days ago when I stumbled on the network manager the wireless networks were all detected the wireless card was not dimmed anymore and everything was working fine. Just like if it never had a problem before... Therefore my puzzlement...

Well it's good to have it working for sure but not just out of the blue...

---

### Post by t0mppa on 2009-09-01
Ok, maybe the default driver for your chip got changed as a result of one of the latter updates, I vaguely remember Ayuthia saying the newer Broadcom chips now get the STA instead of b43 as the default driver, and thus it started working without giving you any hints (before you stumbled upon it).

Anyway, the important thing is that it works now. :)

---

