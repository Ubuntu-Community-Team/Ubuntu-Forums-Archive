---
title: "wireless not recogmized"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by coachmatty on 2009-01-10
I bought an Acer netbook that had XP home. the wireless worked fine. i put Ubuntu 8.10 on it and now the wireless is not recognized at all (no wlan0)

---

### Post by kaffe_02 on 2009-01-10
Click on the hardware drivers under System/Administriation and make sure all of them are selected.

---

### Post by coachmatty on 2009-01-11
I did that:
"No propietary drivers are in use on this system."

---

### Post by sp0nge on 2009-01-11
please open a terminal and enter:
```
lspci
```

Then post the output here.

---

### Post by coachmatty on 2009-01-11
Atheros Communications Inc. 
AR242x 802.11abg wireless pci express adapter (rev 01)

---

### Post by coachmatty on 2009-01-11
driver is now listed and activated but wireless still not working

---

### Post by corysarzotti on 2009-01-24
Same problem but on a PowerBook G4 12"

My output for above was:

me@MacBook:~$ ishw -C network
bash: ishw: command not found
me@MacBook:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 12
       bus info: pci@10:12.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:80084000-80085fff irq:52
  *-network
       description: Ethernet interface
       product: UniNorth 2 GMAC (Sun GEM)
       vendor: Apple Computer Inc.
       physical id: f
       bus info: pci@20:0f.0
       logical name: eth0
       version: 80
       serial: 00:11:24:44:cd:f8
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=gem ip=192.168.1.67 multicast=yes
       resources: iomemory:f5200000-f53fffff irq:41
me@MacBook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

me@MacBook:~$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200] (rev a1)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0001:10:17.0 ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:20:0d.0 ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 81)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)
me@MacBook:~$ a

there is also no device driver program under system.  Unless I am missing something. Thinking of going to Debian or back to OSX.

---

### Post by jbiggs12 on 2009-01-24
I had the same problem on my Penryn MacBook Pro. It used Broadcomm, not Atheros, but I had the very same issues. I restarted my computer, clicked on the networking tab in the title bar, and it was picking up networks. What version of the OS is this? Drivers for Mac are usually supported on Ubuntu.

---

### Post by mrpbjnance on 2009-01-24
I have the same problem  
No drivers shown also  How did you get the drivers installed?

mike@Linux:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:0d.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
00:0f.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:0f.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:0f.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
00:11.0 Multimedia video controller: Zoran Corporation ZR36057PQC Video cutting chipset (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)
mike@Linux:~$ lspci | grep wireless
mike@Linux:~$ lspci | grep Wireless
00:0d.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

---

