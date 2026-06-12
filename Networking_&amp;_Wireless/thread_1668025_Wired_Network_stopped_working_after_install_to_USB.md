---
title: "Wired Network stopped working after install to USB HDD"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by JohnCowan on 2011-01-15
All -

My desktop computer has another Linux distro on it.  Wired networking was working fine.  I wanted to try Ubuntu 10.10 so I installed it on a spare USB HDD.  After install, networking still worked on both distros.

I moved the USB HDD to my win7 laptop and Ubuntu 10.10 booted fine.  Once booted, Ubuntu asked to configure wireless on the laptop.  I tried to do this but it did not work.

Therefore, I moved the USB HHD back to the desktop and booted.  Now the wired network does not work from either Ubuntu or other distro (fedora 14).  And to top it all off, the wired network will not work even from the Ubuntu live CD.

I have checked all connections, switches & cat5 cables to my desktop computer.  I can still access the network and internet from my laptop (in win7) so I do not believe it is an infrastructure issue.  I can confirm that everything works from the cable out of the back of the desktop through to the internet.

Here is the output from the usual troubleshooting commands in Ubuntu 10.10 -

sudo ifconfig -a :```
eth0    Link encap:Ethernet  HWaddr 6c:f0:49:b5:de:0d
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xa000

lo       Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)
```lspci -nn :```

00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0040] (rev 18)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0042] (rev 18)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b3b] (rev 06)
00:1a.1 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b3e] (rev 06)
00:1a.2 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b3f] (rev 06)
00:1a.7 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b36] (rev 06)
00:1d.1 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b37] (rev 06)
00:1d.2 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB Universal Host Controller [8086:3b38] (rev 06)
00:1d.7 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation 5 Series Chipset LPC Interface Controller [8086:3b06] (rev 06)
00:1f.2 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller [8086:3b20] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.5 IDE interface [0101]: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller [8086:3b26] (rev 06)
02:00.0 IDE interface [0101]: JMicron Technology Corp. JMB368 IDE controller [197b:2368]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
```if up eth0 :```
Ignoring unknown interface eth0=eth0.
```cat /etc/network/interfaces :```
auto lo
iface lo inet loopback

```cat /etc/NetworkManager/nm-system-settings.conf :```
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

no-auto-default=6c:f0:49:b5:de:0d,

[ifupdown]
managed=false
```dmesg | grep -e eth0 -e bcm :```
[    1.540246] r8169 0000:03:00.0: eth0: RTL8168d/8111d at 0xf846a000, 6c:f0:49:b5:de:0d, XID 083000c0 IRQ 43
[   24.407077] r8169 0000:03:00.0: eth0: link down
[   24.407215] ADDRCONF(NETDEV_UP): eth0: link is not ready

```lshw -C Network :```
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 6c:f0:49:b5:de:0d
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:43 ioport:ce00(size=256) memory:fbeff000-fbefffff memory:fbef8000-fbefbfff memory:fbe00000-fbe1ffff

```The one thing from the above that seems unusual is the "size: 10MB/s".  Considering that this is a gigabit controller I would expect a higher number.

Does anyone have any ideas as to what has happened?

Thank you

John

---

### Post by rpete on 2011-01-16
Hi, I'm hoping someone will respond to both our posts. I am using 10.04 on a Dell XPS M1530.  My problem is a bit different.  My wired connection was working fine until I downloaded Virtualbox and also installed some VM packages in synaptic manager.  These were the only changes I made to the system so I suspect they interfered with the network somehow.  I notice under Systems preferences Networking connections a Wired Connection 1 and under last used--never, no auto etho0.  I am using my netbook with 10.10 to connect to this forum.  Here is the output of troubleshooting commands for the Dell.

richard@richard-laptop:~$ sudo ifconfig -a 
[sudo] password for richard: 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B) 

richard@richard-laptop:~$ sudo lspci 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c) 
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) 
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02) 
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) 
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) 
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) 
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02) 
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1) 
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) 
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12) 
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12) 
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12) 
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12) 
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02) 
richard@richard-laptop:~$ sudo ifup eth0 
Ignoring unknown interface eth0=eth0. 
richard@richard-laptop:~$ sudo cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 

richard@richard-laptop:~$ sudo cat /etc/NetworkManager/nm-system-settings.conf 
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file: 
# 
# /etc/default/NetworkManager 
# 

[main] 
plugins=ifupdown,keyfile 

[ifupdown] 
managed=false 

richard@richard-laptop:~$ sudo lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c) 
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c) 
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02) 
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02) 
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02) 
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02) 
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02) 
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02) 
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 02) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02) 
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02) 
01:00.0 VGA compatible controller [0300]: nVidia Corporation G86 [GeForce 8400M GS] [10de:0427] (rev a1) 
03:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) 
03:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22) 
03:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12) 
03:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12) 
03:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12) 
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12) 
0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02) 
richard@richard-laptop:~$ 

richard@richard-laptop:~$ sudo lshw -C network 
  *-network UNCLAIMED     
       description: Ethernet controller 
       product: 88E8040 PCI-E Fast Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       version: 12 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0 
       resources: memory:f9ffc000-f9ffffff ioport:de00(size=256) 
  *-network UNCLAIMED 
       description: Network controller 
       product: PRO/Wireless 3945ABG [Golan] Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:0b:00.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0 
       resources: memory:f9eff000-f9efffff 
richard@richard-laptop:~$ 

richard@richard-laptop:~$ sudo dhclient 
Internet Systems Consortium DHCP Client V3.1.3 
Copyright 2004-2009 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/) 

No broadcast interfaces found - exiting.

---

### Post by JohnCowan on 2011-01-16
All -

As an update to my first post.  I have been looking at the issue for the last day.  Another thing that I have noticed is the lights beside the RJ45 plug on the back of the computer are not on.  I am starting to think that this may be a hardware issue.

Has anyone experienced this before?  I find it funny as this is a new motherboard, only a few months old.  The rest of the computer is working fine.

BTW, I have reconnected the USB HDD to my laptop and it booted fine when using the same network cable that was removed from the back of my desktop.

Thanks in advance.

John

---

### Post by pytheas22 on 2011-01-17
**JohnCowan**: I think the problem is probably the line in your /etc/NetworkManager/nm-system-settings.conf file that says "no-auto-default=6c:f0:49:b5:de:0d,"  I'm not sure how that line ended up in there, but it's telling the system not to try to get a connection on your wired interface, which is probably the issue.  It doesn't look like a driver or hardware problem since the interface itself is detected without any issues, according to your output.

To solve the problem, first open that file in a text editor by typing:
```

sudo gedit /etc/NetworkManager/nm-system-settings.conf
```

Then comment out the line in question by putting a # in front of, and save the file.  Finally, reboot and let me know if you're able to get connected (it should just connect automatically).

It is strange that the connection also fails under Fedora and in the live CD, but that could be a separate problem.  Let's try getting it working in your installed Ubuntu 10.10 system before thinking about that.

**rpete**: your problem is different; in your case no driver is claiming the device.  Ubuntu should have a module (named sky2) built in for driving your device, but probably either the system is not auto-loading that module for some reason, or it's failing when it tries to load it.

You can try loading the module manually by typing:

```
sudo modprobe sky2
sudo ifconfig eth0 up
```

After that, wait a few seconds and if all goes as planned, NetworkManager should connect you automatically.  If so, great; we can then set it up so that sky2 will be loaded automatically from now on.  If you still can't get connected after loading sky2, however, please let me know the output of all of the above, as well as:
```

sudo dhclient eth0
dmesg | grep -e sky -e eth0
modinfo sky2
```

---

### Post by rpete on 2011-01-17
Pytheas22 thanks for the reply.  It seems I am missing the sky2 module. I ran the first command with the DSL line plugged in and the module was not found.  Here is the output for the commands but I am not sure how to run dmesg followed by vertical line and the rest.  I don't see that character on my keyboard.

ichard@richard-laptop:~$ sudo modprobe sky2 
FATAL: Module sky2 not found. 
richard@richard-laptop:~$ sudo ifconfig eth0 up 
eth0: ERROR while getting interface flags: No such device 
richard@richard-laptop:~$ sudo dhclient eth0 
Internet Systems Consortium DHCP Client V3.1.3 
Copyright 2004-2009 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/) 

SIOCSIFADDR: No such device 
eth0: ERROR while getting interface flags: No such device 
eth0: ERROR while getting interface flags: No such device 
Bind socket to interface: No such device 
richard@richard-laptop:~$ modinfo sky2 
ERROR: modinfo: could not find module sky2

---

### Post by pytheas22 on 2011-01-17
**rpete**: thanks for the information.  It's very strange that the system thinks the sky2 module doesn't exist, because it definitely exists on my Ubuntu 10.10 system (as well as my 10.04 computer too).  What is the output of:
```

sudo locate sky2
uname -a
```

Also, you're not using a custom-built kernel (i.e., one that you compiled yourself), are you?  And you don't remember installing or uninstalling any kernel packages?  If for some reason you're using a non-standard kernel, it could not have the sky2 module built in for some reason.

---

### Post by rpete on 2011-01-17
Hi, I did not make a custom kernel.  Here is the output for those two commands.  Also, do you need me to run the dmesg  and grep commands? Not sure how.  

richard@richard-laptop:~$ sudo locate sky2 
[sudo] password for richard: 
/lib/modules/2.6.32-21-generic/kernel/drivers/net/sky2.ko 
/lib/modules/2.6.32-27-generic/kernel/drivers/net/sky2.ko 
/usr/src/linux-headers-2.6.32-21-generic/include/config/sky2.h 
/usr/src/linux-headers-2.6.32-27-generic/include/config/sky2.h 
richard@richard-laptop:~$ uname -a 
Linux richard-laptop 2.6.32-27-generic-pae #49-Ubuntu SMP Thu Dec 2 00:07:52 UTC 2010 i686 GNU/Linux

I don't remember installing or uninstalling any kernel packages.  I did look through synaptic manager for Virtual Machine packages and installed a couple, then found Virtualbox website and downloaded that.  After that I lost my connection.

---

### Post by pytheas22 on 2011-01-17
**rpete**: it looks like you do in fact have the sky2 module present, so perhaps it's just a problem with modprobe not knowing about it.  What happens if you try insert the module by giving the full path, using the command:
```

sudo insmod /lib/modules/2.6.32-27-generic/kernel/drivers/net/sky2.ko
```

After this, wait a few seconds and the system will hopefully recognize your device and connect you automatically.  If that fails, please let me know the output of:

```
lsmod | grep sky
dmesg | grep -e sky -e eth
sudo dhclient eth0
```

By the way, the | (or "pipe") character on most keyboards (at least American ones) is above the "enter" key, on the same key as \  Use shift + \ to make |  Or you could always just copy and paste the character if that's easier.

---

### Post by JohnCowan on 2011-01-17
pytheas22 -

Thank you for your response.  Unfortunately I'm out of town for the rest of the week and therefore I am not near my computer.

I will try your suggestions on the weekend and let you know what I get.

Thanks again.

John

---

### Post by rpete on 2011-01-18
Hi, so far my computer is still not recognizing  the sky2 module. Here is the output of the commands you suggested.  The lsmod | grep sky command did nothing.  

richard@richard-laptop:~$ sudo insmod /lib/modules/2.6.32.27-generic/kernel/drivers/net/sky2.ko 
[sudo] password for richard: 
insmod: can't read '/lib/modules/2.6.32.27-generic/kernel/drivers/net/sky2.ko': No such file or directory 
richard@richard-laptop:~$ lsmod grep sky 
Usage: lsmod 
richard@richard-laptop:~$ lsmod 
Module                  Size  Used by 
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon 
font                    7557  1 fbcon 
bitblit                 4707  1 fbcon 
softcursor              1189  1 bitblit 
video                  17375  0 
output                  1871  1 video 
vga16fb                11385  1 
vgastate                8961  1 vga16fb 
psmouse                63245  0 
serio_raw               3978  0 
lp                      7028  0 
parport                32635  2 ppdev,lp 
usb_storage            39585  1 
ahci                   32232  3 
richard@richard-laptop:~$ lsmod | grep sky 
richard@richard-laptop:~$ dmesg | grep -e sky -e eth 
[    0.514257] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> 
richard@richard-laptop:~$ sudo dhclient eth0 
Internet Systems Consortium DHCP Client V3.1.3 
Copyright 2004-2009 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/) 

SIOCSIFADDR: No such device 
eth0: ERROR while getting interface flags: No such device 
eth0: ERROR while getting interface flags: No such device 
Bind socket to interface: No such device 
richard@richard-laptop:~$ lsmod | grep sky

---

### Post by pytheas22 on 2011-01-18
**rpete**: it looks like you had a tiny typo in the command you typed.  It should be:
```

sudo insmod /lib/modules/2.6.32-27-generic/kernel/drivers/net/sky2.ko
```

but it looks like you put a . in between the 32-27 instead of a -  That's why the system said it couldn't find the module.  Please try running the commands in my last post again and let me know if they get you connected.

EDIT: by the way, I notice now also that you're running the pae kernel.  Normally this would only be necessary if you have more than 3 gigabytes of RAM but your processor is only 32-bit; otherwise, if you more than 3 gigabytes of memory and your processor supports 64-bit, you're better off installing 64-bit Ubuntu.  Do you know whether your processor is 32- or 64-bit?  If not, the output of:

```
cat /proc/cpuinfo
```

should say.

I'm beginning to think your ethernet troubles may be related to the pae kernel, and switching to a different kernel might be the simplest solution.

**JohnCowan**: no problem; let me know how it goes when you get a chance to test.

---

### Post by rpete on 2011-01-18
Hi, I am more concerned when I read your suggestion I change kernels. It seems a drastic solution.  This computer has a new hard drive and Lucid Lynx is a clean install. We may be getting ahead of ourselves, but how would a 64 bit kernel change how I use files on external hard drives?  I have 400GB worth of data on one drive. Would it be affected? The new drive is mostly free space. I haven't yet moved files from the external drives onto it.  

I can't remember how much RAM I have.  How do I check?  Here is the corrected command output: Nothing happened when I ran the first command. 

richard@richard-laptop:~$ sudo insmod /lib/modules/2.6.32-27-generic/kernel/drivers/net/sky2.ko 
insmod: error inserting '/lib/modules/2.6.32-27-generic/kernel/drivers/net/sky2.ko': -1 Invalid module format 

richard@richard-laptop:~$ cat /proc/cpuinfo 
processor	: 0 
vendor_id	: GenuineIntel 
cpu family	: 6 
model		: 23 
model name	: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz 
stepping	: 6 
cpu MHz		: 800.000 
cache size	: 6144 KB 
physical id	: 0 
siblings	: 2 
core id		: 0 
cpu cores	: 2 
apicid		: 0 
initial apicid	: 0 
fdiv_bug	: no 
hlt_bug		: no 
f00f_bug	: no 
coma_bug	: no 
fpu		: yes 
fpu_exception	: yes 
cpuid level	: 10 
wp		: yes 
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm ida tpr_shadow vnmi flexpriority 
bogomips	: 4986.61 
clflush size	: 64 
cache_alignment	: 64

---

### Post by pytheas22 on 2011-01-19
**rpete**: the error message about an "Invalid module format" seems to confirm that your kernel is the issue.  Given everything you've posted so far, I suspect what happened in your situation is the following:

1. The last time your ethernet was working, you were using the kernel 2.6.32-27-generic, which has the sky2 module built in and is not a "pae" kernel.

2. Somehow -- perhaps when you were doing things with VirtualBox -- you installed the 2.6.32-27-generic-**pae** kernel.  For some reason this kernel does not have the sky2 module built in, hence why your ethernet is not working when you are booted into that kernel.

3. It looks (from output you posted earlier) like you still have the regular 2.6.32-27-generic kernel installed on your system, but you're currently booting into the 2.6.32-27-generic-pae kernel instead.  You can have as many kernels as you want installed, but when you first turn on your computer you have to select which kernel to boot into at the grub boot menu (if you don't choose it will default to the one at the top of the list, which is probably 2.6.32-27-generic-pae in your case).

I'm not sure why the sky2 module is not built into your pae kernel, but I don't know of any reliable way to get it in place.  So I think the only solution for you will be to boot into a kernel that has sky2 available.

Assuming you still have non-pae kernels installed on your system, booting into one should be as simple as selecting it at the grub boot menu.  (You may need to press escape after turning on your computer in order to display the grub menu; after that, just use the error keys to highlight the kernel you want to boot into, and press enter.)  I'd give that a try and see if the ethernet works under a non-pae kernel.  You can verify the kernel you're using after boot by typing the command "uname -r"; if it mentions "pae" anywhere, you're using the pae kernel; if not, you're not.  If your ethernet works under a non-pae kernel, we can set that to be the default boot choice.

Depending on how much memory you have (you can find out using the command "free -m"), it might make more sense to switch to a 64-bit kernel, which your processor supports (according to the output you posted) and which would not affect in any way your ability to access files on an external drive -- plus 64-bit kernels are actually a little faster in general.  But we can talk more about that once we verify that your ethernet works after you boot into a non-pae kernel.

---

### Post by rpete on 2011-01-19
pytheas22, First things first.  How do I display the grub menu?  I tried pressing esc several times as the system started but nothing happened. I then held down escape but then started to get a beeping sound and released it.  The only options I see are press f2 for set up and f12 for boot sequence but those do not show the kernals.  Boot sequence shows Internal Hard drive, CD/DVD ROM Drive, etc. I saw a post in which a person could only see the grub menu and could no longer see the Splash screen. 

Changing to 64 bit sounds less bothersome, but I did hear that it might mess up the formatting of documents.  I have 4GB of free memory.

---

### Post by pytheas22 on 2011-01-19
**rpete**: sorry, my mistake.  Apparently in the modern version of grub you have to hold down shift to get the boot menu, not escape (I haven't done this in a while so I wasn't aware of the change, but according to the [Ubuntu wiki]("https://help.ubuntu.com/community/Grub2") shift is the new key).  Please try it with shift and hopefully it will work.

---

### Post by rpete on 2011-01-19
pytheas22  It worked!  During startup I went into the Grub menu and at the top was the generic pae kernel.  I arrowed down to generic kernel and pressed enter and waited for it to boot.  Then I plugged in my ethernet connection and it worked.  I disconnected, restarted, connected again and it no longer worked. I went to terminal and typed uname -r and it indicated the generic pae kernel. So it seems we have to find a way to make sure the system boots from the generic kernel.  I came across thread 1505217 from 2009 which describes a similar problem.  One curious thing.  When I ran the command lshw -C network it listed three connections eth0 wlan0 and virtualboxnet0.

---

### Post by pytheas22 on 2011-01-19
**rpete**: good to hear you've finally had some success!  And at least now we know that the pae kernel is the issue.

So there are now three different options for you which should provide a permanent solution:

1. edit your boot menu so that the pae kernel is no longer the default choice.  This way it will still be available if you want to select it manually, but by default your system will boot into a non-pae kernel.  To configure this, open the grub configuration template file in a text editor by typing:

```
sudo gedit /etc/default/grub
```

Then edit the value of the variable GRUB_DEFAULT so that it corresponds to the line number in the boot menu containing the kernel you want to boot to, with 0 being the entry at the top of the list.  So if the kernel that worked for you was third from the top in the boot menu, you would set GRUB_DEFAULT to 2.

When you're done making changes, save the file, then run:

```
sudo update-grub
```

for changes to take effect.

2. remove the pae kernel completely.  Assuming you installed it from the Ubuntu Software Center, you should be able to do this by searching for the package linux-image-generic-pae (I think, though that may not be the exact name of the package and I'm unable to check right now) and removing it.  If it tells you that removing this package will force the removal of other packages as well, be sure you know that you can remove them safely before agreeing.

Removing the package will automatically delete its entry from your boot menu.

3. reinstall Ubuntu using the 64-bit version, which will give you a 64-bit kernel by default.  The advantage here is that you'll be able to take full advantage of your 4 gigabytes of RAM while also having working ethernet.  If you go with options 1 or 2 above, you'll be using a non-pae 32-bit kernel, which will only be able to address about 3 gigabytes of the RAM due to fundamental architectural limitations which apply to all operating systems.  (If you want to read about why this is, there's a decent explanation [here]("http://www.dansdata.com/askdan00015.htm").)

A 64-bit kernel can use up to something like 192 gigabytes of RAM, so it would allow you to take full advantage of your computer's resources.  64-bit kernels also generally provide slightly faster computations.  In my view, there's really no reason not to use a 64-bit kernel these days as long as your process supports it.  It won't affect any of your data at all; a 64-bit kernel will be able to read and write all files just as well as a 32-bit one.  I've never heard of 64-bit kernels corrupting documents.

Theoretically you could install a 64-bit kernel on your existing system, but that might get messy and if you want to go this route, it would probably be a lot easier just to reinstall Ubuntu from scratch using the 64-bit version.  You can download the 64-bit installation CD (or USB stick, or whatever) by going to [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) and selecting the 64-bit option.  (The website recommends the 32-bit version, but I'm pretty sure Ubuntu does that only to make it easier for users who don't know whether their processor will support 64-bit; there's really no other reason why 32-bit would be preferable, as far as I know.)

Of course, reinstalling will erase any date stored on the partitions of your hard drive which you reformat during the installation, so you'd want to back that up first.

Sorry to write so much, but hopefully this sums up what you can do to make the solution permanent.  When you've decided which route you want to take, let me know if you have any trouble getting there.

---

### Post by rpete on 2011-01-20
pytheas22  I followed your instructions for option 1 and all went well.  Grub is now booting from the third kernel from the top, the generic one, and my ethernet connection works fine.  I would mark this solved but it is JohnCowan's thread.  Thanks for all your help. I will postpone changing to the 64 bit kernel. Right now I don't want to risk even the slightest problems with my computer, but maybe later.

---

### Post by rpete on 2011-01-20
pytheas22  I followed your instructions for option 1 and all went well.  Grub is now booting from the third kernel from the top, the generic one, and my ethernet connection works fine.  I would mark this solved but it is JohnCowan's thread.  Thanks for all your help. I will postpone changing to the 64 bit kernel. Right now I don't want to risk even the slightest problems with my computer, but maybe later.

---

### Post by pytheas22 on 2011-01-20
**rpete**: good to hear it worked out.  The one thing you might want to keep in mind is that when you run Ubuntu updates it might install newer kernel packages if they are available.  I'm not sure whether they'll be pae kernels or not, or whether they'll contain the sky2 module (they should but you never know).  Buu either way the updates should leave all of your existing kernel packages in place, so you can always boot into an older kernel if you get a newer one that doesn't work.

Because adding kernels may change the order of entries in your boot list, though, you might have to edit the /etc/default/grub file again after running updates to make the set the default kernel appropriately.

---

### Post by pytheas22 on 2011-01-20
**rpete**: good to hear it worked out.  The one thing you might want to keep in mind is that when you run Ubuntu updates it might install newer kernel packages if they are available.  I'm not sure whether they'll be pae kernels or not, or whether they'll contain the sky2 module (they should but you never know).  Buu either way the updates should leave all of your existing kernel packages in place, so you can always boot into an older kernel if you get a newer one that doesn't work.

Because adding kernels may change the order of entries in your boot list, though, you might have to edit the /etc/default/grub file again after running updates to make the set the default kernel appropriately.

---

### Post by JohnCowan on 2011-01-24
pytheas22 -

I tried your suggestion below.

> **pytheas22 said:**
> **JohnCowan**: I think the problem is probably the line in your /etc/NetworkManager/nm-system-settings.conf file that says "no-auto-default=6c:f0:49:b5:de:0d,"  I'm not sure how that line ended up in there, but it's telling the system not to try to get a connection on your wired interface, which is probably the issue.  It doesn't look like a driver or hardware problem since the interface itself is detected without any issues, according to your output.

To solve the problem, first open that file in a text editor by typing:
```

sudo gedit /etc/NetworkManager/nm-system-settings.conf
```Then comment out the line in question by putting a # in front of, and save the file.  Finally, reboot and let me know if you're able to get connected (it should just connect automatically).

It is strange that the connection also fails under Fedora and in the live CD, but that could be a separate problem.  Let's try getting it working in your installed Ubuntu 10.10 system before thinking about that.

Unfortunately, it did not fix the problem.  The reason I was thinking that it was a hardware issue is because I do not get any of the lights on the back of the ethernet port.  Unless the firmware for the network card was changed somehow.  Is this possible?

Thanks

JohnCowan

---

### Post by pytheas22 on 2011-01-24
**JohnCowan**: I doubt it's a hardware problem because all of the output you posted in your first post suggests that Ubuntu "sees" the device and has a driver for it.  If there were a hardware problem, I'd expect Ubuntu not to recognize it at all.  The light on the port is probably not illuminating simply because the device is being left "down," meaning Ubuntu is not asking for a connection on it; usually the lights only turn on when traffic is being sent in or out, and that can only happen if the device is up.

I still think a misconfiguration with NetworkManager is at the root of the problem here.  But to make sure, let's try shutting down NetworkManager altogether and asking for a connection manually.  If NetworkManager is the culprit, this should make it clear.

You can disable NetworkManager by typing:
```

sudo /etc/init.d/network-manager stop
```

(Note that you'll probably get a confusing message that starts with "Rather than invoking...blah blah blah"; you can ignore this.)

Then bring the ethernet device up and try to get an IP address on it manually by typing:
```

sudo ifconfig eth0 up
sudo dhclient eth0
```

If this works, you'll get some information on the command line about which IP address was set, and you should now be able to browse websites, etc.  If it fails, please post all of the output from the commands above, along with:
```

dmesg | grep -e eth -e r8169 -ie network
ifconfig
ifconfig -a
```

Rebooting the computer will reset everything back to the default and turn NetworkManager back on.  But if a manual connection works we'll have narrowed down the source of the problem and can try some other things to fix NetworkManager.

---

### Post by JohnCowan on 2011-01-24
pytheas22 -

As you will see, for some unknown reason everything has changed since last week.  I am now now longer even seeing eth0.  Here are the results of the commands you requested.  I did stop Network Manager as you requested first.  I tried it both with the "sudo /etc/init.d/NetworkManager stop" and the "sudo service network-manager stop" as suggested by the *blah blah blah* when using the init script.

> **pytheas22 said:**
> 
sudo ifconfig eth0 up

```
john@jupiter:~$ sudo ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device
john@jupiter:~$ 

```> **pytheas22 said:**
> sudo dhclient eth0

```
john@jupiter:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
john@jupiter:~$ 

```> **pytheas22 said:**
> dmesg | grep -e eth -e r8169 -ie network

```
[    8.404156] type=1400 audit(1295901222.991:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=731 comm="apparmor_parser"
[   31.536551] type=1400 audit(1295901246.191:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1004 comm="apparmor_parser"

```> **pytheas22 said:**
> ifconfig

```
john@jupiter:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57889 (57.8 KB)  TX bytes:57889 (57.8 KB)

john@jupiter:~$

```> **pytheas22 said:**
> ifconfig -a

```
john@jupiter:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44641 (44.6 KB)  TX bytes:44641 (44.6 KB)

john@jupiter:~$

```As an aside, I was using this USB HDD to run Ubuntu on another computer while I was on my trip.  During that time I had no issues with connecting to a wired connection.

What do you think?

JohnCowan

---

### Post by pytheas22 on 2011-01-25
**JohnCowan**: hmmm, given the output in your most recent post, it does now look like a hardware issue.  Ubuntu doesn't detect the hardware as being present at all.  This is strange because it definitely was a week ago, but if the hardware is flaking out, it could be that it gets detected on some boots, and not on others.

You might have two problems going on here.  The first could be with the hardware, and the second with a configuration issue inside Ubuntu itself.  You won't be able to fix the second problem until you sort out the first one.

I know you've checked the cable connection, etc., but have you actually opened up the desktop to make sure everything internally is connected properly?  If the ethernet card is a standalone PCI device, I'd try reseating it; if it's built into the motherboard, make sure everything else is hooked up properly.

If the ethernet card is part of the motherboard, it's also possible that it's simply being disabled in BIOS, so I'd take a look there.  Not all BIOS programs have an on option to enable or disable onboard ethernet but better boards usually do.

Please try these things and let me know how it goes.  When the card is properly connected to the rest of the system, the output of the command "lspci -nn" should contain the line "03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)"  If that line's not present, it's a pretty sure thing there's a hardware issue.

P.S.: I'm traveling internationally tomorrow and may not get a chance to catch up with my Internet life until later in the week, so please don't be offended if I take a little while in responding to your next post.  I'll get to it as soon as I'm reasonably recovered from the jetlag.

---

