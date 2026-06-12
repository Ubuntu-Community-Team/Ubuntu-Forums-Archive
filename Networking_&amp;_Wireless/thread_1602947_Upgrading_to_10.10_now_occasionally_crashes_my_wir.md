---
title: "Upgrading to 10.10 now occasionally crashes my wireless network"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by Shoulders on 2010-10-22
Hi,
 
I have an HP 311c netbook which was dual booted XP home and Ubuntu 10.04. Everything worked fine apart from the internal wireless modem (the only reason I needed XP as it worked under Windows)
 
I then upgraded to 10.10 and that started my network problems.
 
I upgraded Ubuntu using terminal and update-manager, which went ok. The network was identified, but more often than not it now seems to crash the network (and seems to happen sporadically too) - seems to be at some stage whenever the netbook is on now. This then prevents all other PCs/Ipods from accessing the internet. The only way to recover is to reboot my wireless network and the internet modem (and shutdown the netbook).
 
I got so infuriated with it that I clean installed from a USB key I created, but this hasn't helped.
 
Wireless network runs fine with all other PCs and IP equipment
 
Network: Linksys 11 B
Internet modem Virgin Media
 
One strange thing that happened when I upgraded, but seems to have now disappeared, is that I managed to get it to identify and actually use the internal modem, although that 'Mobile Internet' option under Network Manager has now disappeared from the list, so I cannot activate it...
 
Please help... (on two counts: network compatibility, and mobile internet modem usage)

---

### Post by P4man on 2010-10-22
Do I understand correctly that you have both issues with Wifi and an internal 3/4G modem ? Can you post the output of 

```
lspci
```

and 

```
lsusb
```

and 

```
lshw -C network
```

For starters?

---

### Post by Shoulders on 2010-10-22
Hi P4man,
 
Yes you are correct, I do have issues with both.
 
[FONT=Times New Roman][SIZE=3]lspci[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]02:00.0 VGA compatible controller: nVidia Corporation ION LE VGA (rev b1)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]lsusb[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Bus 004 Device 003: ID 03f0:2a1d Hewlett-Packard [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Bus 002 Device 002: ID 5986:0182 Acer, Inc [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Bus 001 Device 003: ID 03f0:241d Hewlett-Packard Gobi 2000 Wireless Modem (QDL mode)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3]lshw -C network[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]WARNING: you should run this program as super-user.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]  *-network               [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       description: Ethernet interface[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       product: MCP79 Ethernet[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       vendor: nVidia Corporation[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       physical id: a[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       bus info: pci@0000:00:0a.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       logical name: eth0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       version: b1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       serial: 00:26:9e:84:17:38[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       width: 32 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       clock: 66MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       capabilities: bus_master cap_list ethernet physical[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       configuration: broadcast=yes driver=forcedeth driverversion=0.64 latency=0 maxlatency=20 mingnt=1 multicast=yes[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       resources: irq:23 memory:d3106000-d3106fff ioport:30e0(size=8) memory:d3109000-d31090ff memory:d3109300-d310930f[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]  *-network[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       description: Wireless interface[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       product: BCM4312 802.11b/g LP-PHY[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       vendor: Broadcom Corporation[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       physical id: 0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       bus info: pci@0000:03:00.0[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       logical name: eth1[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       version: 01[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       serial: 90:4c:e5:15:55:06[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       width: 64 bits[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       clock: 33MHz[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       capabilities: bus_master cap_list ethernet physical wireless[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.102 latency=0 multicast=yes wireless=IEEE 802.11[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]       resources: irq:16 memory:d3000000-d3003fff[/FONT][/SIZE]

 
Thanks for taking the time :)

---

### Post by P4man on 2010-10-22
OKay, lets start with the wifi. That is probably easy. Here is a howto for your card:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20BCM43xx%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20BCM43xx%20drivers)

You check beforehand by running

lspci -vnn | grep 14e4

and matching the ID with this list:
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

---

### Post by Shoulders on 2010-10-22
Great stuff, I went through the docs and have been testing it this afternoon with no drop outs at all....
 
I think the problem was I was using the Broadcom STA driver and not the B43 one...
 
Brilliant, thank you P4man any ideas on my next problem i.e my internal wireless modem?
 
:)

---

### Post by P4man on 2010-10-22
Good, thats the easy problem solved.

As for the modem... I dont have any exposure to 3G modems, and google isnt too helpful for yours. But what I did read makes me wonder how it could have worked even for a moment, without fetching drivers or at least the firmware.

Have a look here:

[http://www.codon.org.uk/~mjg59/gobi_loader/](http://www.codon.org.uk/~mjg59/gobi_loader/)

[I]
These devices appear in an uninitialised state when power is applied and require firmware to be loaded before they can be used as modems. gobi_loader adds a udev rule that will trigger loading of the firmware and make the modem usable. [/I]

Maybe it did work because you had windows hibernated rather than shut down, and the firmware was still loaded when you booted ubuntu? You could try that again for the heck of it, but be adviced its a very bad idea to have windows hibernated if you intend to mount the windows file system in ubuntu. And someone else recently had the opposite problem, if windows was hibernated his ethernet controller would no longer work in ubuntu. Just FYI.

Anyway, if you read that page, then it would appear you need to patch and compile your own kernel, that is beyond my knowledge. But if it has worked once, then I suspect ubuntu 10.10 already includes that patch, and Id skip that part.  Maybe you can skip most the rest too if it turns out its just a matter of loading the firmware.

---

