---
title: "WiFi but no Internet"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by HHBones on 2010-02-17
Hi, I am new to Ubuntu, but because of my familiarity with Vista's Command Prompt, I was able to adapt easily. But there was a problem. My WiFi card didn't work. As it turned out, I was missing drivers. So I plugged into my dad's Gigabit Ethernet port and got ndiswrapper.
That worked well, and my wireless card is working. The problem is that I can access the network in my house, but not the Internet. Everybody else (running Windows) can access the Internet wirelessly. But I have to steal my dad's wired work line. Is there any way to solve this? If anybody needs info about my computer, here it is:

OS: Ubuntu 9.10 Karmic Koala
Computer: (Laptop) Dell Vostro 1000
Wireless card: Dell 1390 wireless
Router: Netgear... some model or another

---

### Post by Crafty Kisses on 2010-02-17
I need a bit more information, so go into a terminal **(Applications->Accessories->Terminal)** and run the following commands:
```
lspci
lsusb
lshw -C network
```
Copy and paste the results of each command back here at the forums then I or somebody else can help you further.

---

### Post by HHBones on 2010-02-18
> **Crafty Kisses said:**
> I need a bit more information, so go into a terminal **(Applications->Accessories->Terminal)** and run the following commands:
```
lspci
lsusb
lshw -C network
```Copy and paste the results of each command back here at the forums then I or somebody else can help you further.

Here it is:

henry@Henry-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)


henry@Henry-laptop:~$ lsusb
Bus 001 Device 002: ID 1058:070b Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

henry@Henry-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth2
       version: 01
       serial: 00:1f:3a:a6:b7:14
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=10.42.43.1 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:cb:c2:a2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
       resources: irq:21 memory:c0300000-c0301fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


Also, while messing around in the User Preferences panel, I noticed that the 'privileges' panel was gray to show that I can't access it. And, lo and behold, one of the unchecked options was that I can't connect to the Internuts through a modem. Does anybody know how to change that? Or how to make your user the super-user?

---

### Post by hj_ebfe on 2010-02-18
Run the command

sudo apt-get install b43-fwcutter

That will install the restricted device driver for the broadcom card.  Then go to System->Administration->Hardware Drivers and you should  see the broadcom driver available. Disable and then reenable it  followed by a reboot. Hopefully it will work after that.

---

### Post by HHBones on 2010-02-18
> **hj_ebfe said:**
> Run the command

sudo apt-get install b43-fwcutter

That will install the restricted device driver for the broadcom card.  Then go to System->Administration->Hardware Drivers and you should  see the broadcom driver available. Disable and then reenable it  followed by a reboot. Hopefully it will work after that.

I have the drivers working, the problem is that Ubuntu isn't letting me connect to the Internet through WiFi even though I am connected to the network.

---

### Post by hj_ebfe on 2010-02-18
In that case, I would check the connection between the wireless router and the cable modem/internet. Often a restart for them both will clear up any DHCP/other issues that have occurred.

---

### Post by HHBones on 2010-02-18
> **hj_ebfe said:**
> In that case, I would check the connection between the wireless router and the cable modem/internet. Often a restart for them both will clear up any DHCP/other issues that have occurred.

No, all of the other Windows-based computers in my house have complete wireless access.

---

### Post by HHBones on 2010-02-18
Do you guys know how to change your User Privileges or how to make yourself Super-User?

EDIT: Tried that, didn't work. Any more ideas?

---

### Post by HHBones on 2010-02-18
I'll try installing LXDE Linux inside a virtual machine to see if LXDE can connect to the Internuts.

---

### Post by Iowan on 2010-02-18
> **HHBones said:**
> Do you guys know how to change your User Privileges or how to make yourself Super-User?

Hope [this]("https://help.ubuntu.com/community/RootSudo") helps.
Post results of **route -n** and contents of */etc/resolv.conf*

---

### Post by fedfan on 2010-02-19
Hi, Did you get any success? Please share the solution as I am having the same issue.

Thanks.

---

