---
title: "wubi doesnt detect wireless usb adapter"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by mebinte on 2009-12-11
hey all. . i couldnt get the wireless usb adapter to work. its an airlink n adapter. i gogoled a bit and extracted this from terminal. hope it helps. also, i installed the wubi that came with the cd, i dont know if its 64bit wubi. xD

qwerty@ubuntu:~$ **sudo lshw -C network**
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:15:5e:a9
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:de00(size=256) memory:fdbff000-fdbfffff(prefetchable) memory:fdbe0000-fdbeffff(prefetchable) memory:fdb00000-fdb0ffff(prefetchable)
 [B] *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:6a:3f:c4:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn[/B]
qwerty@ubuntu:~$** uname -a**
Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
qwerty@ubuntu:~$ **lspci**
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV790 [Radeon HD 4800 Series]
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
qwerty@ubuntu:~$ **lsusb**
Bus 002 Device 003: ID 14b2:3c27 Atheros Communications Inc 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
qwerty@ubuntu:~$** lshw -classnetwork**
Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.14)

format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)

---

### Post by mebinte on 2009-12-11
also, i forgot to mention that i did a fresh ubuntu install before the this usb adapter worked before, so i dont think its a compatibility problem

---

### Post by mebinte on 2009-12-11
i just tried ubuntu 9.04 wubi. the wireless adapter worked for that -.-
does anyone know the problem? i am upgrading now from 9.04 to 9.10, its dling like 1217 files and says it will take 2 hrs.

i dont know if the upgrade will mess it up again. is there anyway to fix the problem in 9.10? also, my ati fan is roaring, how can i slow the fan down aswell
thanks

---

### Post by mebinte on 2009-12-11
srry, i forgot to include the working one on 9.04
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:15:5e:a9
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 00:1d:6a:3f:c4:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.103 multicast=yes wireless=RT2870 Wireless
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: c2:43:0b:83:d0:31
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by mebinte on 2009-12-12
after downloading and installing  1217 files and then removing 47ish files, i restarted ubuntu, and the same thing happened. anyway to fix this for 9.10?,

 i prefer using it rather then 9.04 since it recognized my dell monitor and uses the whole screen

---

### Post by mebinte on 2009-12-12
anyone? :(

---

### Post by mebinte on 2009-12-12
omg, someone on this section should know :(

i installed ubuntu on sun virtualbox. the connection worked there too, but it showed shows as autoeth0, so i doubt its wireless. 

i still need to get it working on 9.1 without vmware. :(

---

### Post by mebinte on 2009-12-13
bump :(
let me know if i need to provide any other info.

---

### Post by mebinte on 2009-12-14
128 view and no replies :( 
bump

---

### Post by mebinte on 2009-12-14
bump. :(

---

### Post by mebinte on 2009-12-14
is there anyway to dl any updated files and transfer them via usb stick to ubuntu and them install them from there?.

---

### Post by mebinte on 2009-12-16
> **mebinte said:**
> bump. :(.

---

### Post by bkratz on 2009-12-16
You might have a look at this to see if it is any help

[http://ubuntuforums.org/showthread.php?t=1342593&highlight=peepingtom](http://ubuntuforums.org/showthread.php?t=1342593&highlight=peepingtom)

---

### Post by mebinte on 2009-12-16
> **bkratz said:**
> You might have a look at this to see if it is any help

[http://ubuntuforums.org/showthread.php?t=1342593&highlight=peepingtom](http://ubuntuforums.org/showthread.php?t=1342593&highlight=peepingtom)

my driver is awll6070 :( . i installed ndiswrapper via usb with the ndiswrapper common files. + graphics input thing. it doesnt recognize the inf files in the awll6070 :(

---

### Post by bkratz on 2009-12-16
> **mebinte said:**
> my driver is awll6070 :( . i installed ndiswrapper via usb with the ndiswrapper common files. + graphics input thing. it doesnt recognize the inf files in the awll6070 :(

I went to the website and downloaded the windows driver and the driver name is RT2870, hence the earlier email.  Since you using ndiswrapper there are two different drivers there one for 32 bit and one for 64 bit, did you use the right one?

---

### Post by mebinte on 2009-12-16
> **bkratz said:**
> I went to the website and downloaded the windows driver and the driver name is RT2870, hence the earlier email.  Since you using ndiswrapper there are two different drivers there one for 32 bit and one for 64 bit, did you use the right one?

ha, i got it working after watching a youtube video
i got it working, ^^. before i tried niswrapper with the different inf in the awll6070 folder. (vistax64->netr28ux.inf,vistax86->netru.inf,winxp86&64->rt2870.inf) i rebooted and they still didnt work. the porblem was i had the usb connected the whole time

solution for othersfor 64bit:
1)download x64 rt2870 drivers +ndiscommonamd64,ndiswrapperamd64,ndisgthamd64
2)save all to usb stick. disconnect usb adapter and reboot
3) let ubuntu install. then install the ndis stuff and add the driver
4)plug usb adapter and input the router password ^^

i rebooted it again after updating ubuntu. it recognized my wireless adapter and connection automatically.:guitar: so far so good :P

[SIZE=6]SOLVED[/SIZE]

---

### Post by bkratz on 2009-12-16
Just curious, what utube video were you watching? Also, the best way to mark it solved (to help the most people find it) is to go to the thread tools and select solved. It will then show up on the main listing.

---

### Post by mebinte on 2009-12-16
> **bkratz said:**
> Just curious, what utube video were you watching? Also, the best way to mark it solved (to help the most people find it) is to go to the thread tools and select solved. It will then show up on the main listing.
[http://www.youtube.com/watch?v=gk8g1vr2kpA](http://www.youtube.com/watch?v=gk8g1vr2kpA)
i just learned to disconnect the usb adapter from that video. xD

---

