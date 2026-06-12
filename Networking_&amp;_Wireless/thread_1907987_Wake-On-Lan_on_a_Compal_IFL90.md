---
title: "Wake-On-Lan on a Compal IFL90"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by borg0 on 2012-01-12
Hi forum,

I am desperately trying configure Wake-On-Lan (WOL) on a headless installation of Ubuntu 11.04 (natty) on a no-name laptop based on a Compal IFL90 barebone. The setup is headless in the sense that the laptop's GFX card is broken and I am therefore only able to access the machine via SSH. The laptop has a Broadcom NetLink BCM5787M Gigabit Ethernet adapter. 

```

borg@sokrates:~$ lspci | grep 04:00.0
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)

```I have followed exactly the instructions from [1] and [2] (in german, sorry) in order to activate WOL but it doesn't work. Due to the broken GFX card I am not able to access the BIOS but according to the information in [3] the IFL 90's BIOS does not offer an option to enable WOL anyway and it is enabled by default.

This is also supported by the fact that in my current configuration the LED at the machine's ethernet port is active and the router indicates an active link (active LED) even when the machine is not running. I have ensured that the magic packet arrives at the machine when it is running with tcpdump.

```

borg@sokrates:~$ ifconfig eth0 | grep HWaddr
eth0      Link encap:Ethernet  HWaddr 00:1b:38:2b:aa:fd  

```I am trying to wake the machine up via a wireless connection from a Thinkpad W510 with

```

fabian@platon:~$ sudo etherwake -i wlan0 -D 00:1b:38:2b:aa:fd
The target station address is 0:1b:38:2b:aa:fd.
Sendto worked ! 116.

```The network interface is configured statically in /etc/network/interfaces

```

borg@sokrates:~$ sudo cat /etc/network/interfaces
auto eth0
iface eth0 inet static
    address 192.168.0.101
    netmask 255.255.255.0
    gateway 192.168.0.1
    pre-down /usr/sbin/ethtool -s eth0 wol g

```and WOL seems to be configured properly

```

borg@sokrates:~$ sudo ethtool eth0
    Supports Wake-on: g
    Wake-on: g

``````

borg@sokrates:~$ cat /proc/acpi/wakeup 
Device    S-state      Status   Sysfs node
HDEF      S4    *disabled  pci:0000:00:1b.0
PXSX      S5    *enabled   pci:0000:04:00.0

```I tried all troublyshooting options from [1] and [2] - nothing helped.

Any help on this matter is greatly appreciated as I really want to enable WOL for this machine.

Is there anything I can do to narrow down the problem?
Does anybody have any ideas for further things I could try?

Thanks alot!
borg


References:
[1] [https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)
[2] [http://wiki.ubuntuusers.de/Wake_on_LAN](http://wiki.ubuntuusers.de/Wake_on_LAN)
[3] [http://forum.notebookreview.com/sager-clevo/574332-how-enable-wake-lan-compal-2090-ifl-90-a.html](http://forum.notebookreview.com/sager-clevo/574332-how-enable-wake-lan-compal-2090-ifl-90-a.html)

---

### Post by JRV on 2012-01-12
Try:
```

sudo apt-get install wakeonlan
wakeonlan MAC_ADDRESS

```
It works for Me, I have ethtool installed but I don't know for sure if it is necessary.
Also, make sure it is enabled. Some BIOSes have it disabled as default.

---

### Post by borg0 on 2012-01-12
Thanks for your reply. 

I have already tried the wakeonlan command. It doesn't work either and as far as I know it does exactly the same as etherwake (with the benefit of not needing superuser rights).

The problem is most probably related to the machine I'm trying to wake up. As I already said WOL is supposed to be enabled by default on the Compal IFL90 [3] but unfortunately I'm not able to check that because the machine has a broken GFX card and I'm not able to access the BIOS.

But the router indicates an active link even when the machine is shut down and the little LED on the ethernet port is also active. I'm therefore pretty sure that WOL is enabled properly. When I send magic packets to the (halted) machine with "etherwake" (or "wakeonlan") I can see them passing the router (the LED blinks) and I can also see the LED at the ethernet port of the IFL90 blink for each packet I send. So the machine seems to actually (at least in some sense) receive the packet... ..but it doesn't wake up.

What might also be important is that this is probably not a standard installation of Ubuntu Server 11.04. I recovered the machine (no GFX card -> no output to the screen) by performing an unattended install of a minimal Ubuntu Server 11.04 system (only about 20M on the installation CD) that only shipped the OpenSSH server. I created the CD at [1] and the system automatically installed several further packages from the standard Ubuntu repositories directly after the installation. So it might be a standard installation or some packages might be missing.

Some other things I already tried:

1. I also read on launchpad that some people had problems with WOL when network-manager and network-manager-gnome where installed but I think that this was related to Oneiric. Furthermore none of these packages is installed on my machine.

2. In [2] it says that sometimes WOL does only work when the machine is shut down from another OS or from GRUB. It is proposed to create a GRUB entry that simply halts the machine and instead of shutting down, restart the machine to run the GRUB entry that finally halts it. Unfortunately I could not really try this because the described technique did not work on my system. After rebooting the system seemed to hang in GRUB and did not finally shut down. What I did try is to start and quickly shut off the machine by hand several times but that also didn't work.

Any help on tracking this down is greatly appreciated!
borg


[1] [http://www.instalinux.com/](http://www.instalinux.com/)
[2] [http://wiki.ubuntuusers.de/Wake_on_LAN](http://wiki.ubuntuusers.de/Wake_on_LAN)
[3] [http://forum.notebookreview.com/sager-clevo/574332-how-enable-wake-lan-compal-2090-ifl-90-a.html](http://forum.notebookreview.com/sager-clevo/574332-how-enable-wake-lan-compal-2090-ifl-90-a.html)

---

