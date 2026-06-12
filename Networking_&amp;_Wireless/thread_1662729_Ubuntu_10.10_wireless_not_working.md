---
title: "Ubuntu 10.10 wireless not working"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by APologies-- on 2011-01-08
Hi, 

I want to apologise in advance for posting such a common problem, however for the last 5 hours I have been searching for \ fix for this and have yield no luck as of yet. Thus down to some more personal help. 
Another thing is I'm not exactly LInux savvy so I have very little skill with the terminal, however I can follow instructions extremely well. 
And that sounds like my CV, so I'll get straight to it.

Thanks in advance. 

I've downloaded all the drivers and have an ethernet connection working however as I have an INSPIRON 1545, the network card is shoddy for LInux and I can't get the wireless working AT ALL. 


Here are some diagnostics for you:

 **lshw -C network**

  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:06:d1:25
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.65 latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:5f:49:1e:04
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-24-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
[B]
dmesg | grep -e tg3 -e ssb -e wlan0[/B]

[  258.469573] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[  258.469602] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[  258.469627] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[  258.469653] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[  258.516604] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[  330.933895] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[B]ifconfig -a

[/B]grant@Ubuntu-Studio:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:ae:06:d1:25  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:aeff:fe06:d125/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9407 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9140428 (9.1 MB)  TX bytes:1448621 (1.4 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64154 (64.1 KB)  TX bytes:64154 (64.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:49:1e:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:22:5f:49:1e:04  
          inet addr:169.254.3.72  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

[B]route

[/B]grant@Ubuntu-Studio:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 eth0

[B]lspci
[/B]
grant@Ubuntu-Studio:~$ lspci
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
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)



Need any more just ask.

THanks in advance.

---

### Post by APologies-- on 2011-01-08
Also - whenever I plug my Ethernet in it switches the name of WLAN0 to ETH1....

---

### Post by smuthavarapu on 2011-01-08
Hi, Try this post, might help you

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

I have BCM4311 and Live USB solution worked for me. But Check the First post and try the steps, its worth Trying.

Best of Luck

---

### Post by APologies-- on 2011-01-08
> **smuthavarapu said:**
> Hi, Try this post, might help you

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

I have BCM4311 and Live USB solution worked for me. But Check the First post and try the steps, its worth Trying.

Best of Luck

Hi,

thanks for the input but I managed to fix it before reading the post :(
[B]TO PEOPLE WITH A SIMILAR PROBLEM THIS IS HOW I FIXED IT
[/B]this guide is NOT my own, but I also can't remember the username of the person who posted it. if someone can tell me I'll happy put his name in it:

(Before reading this I offer another solution for the wireless card not working. However this will ONLY work if you have an Ethernet plugged in and working. My main problem was not being able to properly enable my wireless connection as the Network Manager sucks - so if you're having any problems at all (and this is how I fixed my connection) **type this into terminal: **[SIZE=2]_*sudo apt-get install wicd-gtk *_  this adds a program into **Menu **> **Internet** called **WICD**. It's a really easy version of network manager which detects the wireless card (given it's installed, see below) and lets you set it as default. If you have any queries I'll try to answer with all my knowledge on: [email]Jones.gdj@gmail.com[/email] as I understand for noobs, like myself, this like a new form of language.)[/SIZE]
Good luck!



Broadcom hardware only. Credit to respective solution providers included below. Feel free to chime in if I've missed something.

[B]Broadcom BCM4311/12/21/22 Hardware (STA driver):
NOTE: ASSUMES FRESH INSTALL. FOR LAPTOPS, ONCE THE SYSTEM REBOOTS AFTER INSTALL, REBOOT AGAIN
AND TOGGLE THE WIRELESS BUTTON (YES, IT COULD BE THAT EASY).[/B]

Plug into the network via cable:
**IF WIRED CONNECTION WORKS:**
Open System -> Admin -> Update Manager
Check for updates, install, and reboot
After reboot, open System -> Admin -> Hardware Drivers
Look for "Broadcom STA wireless driver";
**IF DRIVER IS PRESENT AND ACTIVATED:**
Remove network cable, toggle wireless button, and log into network.
** IF DRIVER IS PRESENT BUT NOT ACTIVATED:**
Activate and reboot;
After reboot, remove network cable, toggle wireless button, and log into network.
**IF DRIVER IS NOT PRESENT:**
Open System -> Admin -> Synaptic Pkg Mgr
Search for "bcmwl-kernel-source" (if not available, move to step 2)
Right-click and mark for installation
Apply changes and reboot.
Repeat steps 1.3-1.4.2
**IF WIRED CONNECTION DOES NOT WORK:**
From LiveCD (solution provided by jomtois here - edited for clarity):
Open Sytem -> Admin -> Synaptic Package Mgr
Ensure 9.10 LiveCD is in the drive
In Synaptic Package Mgr, open Settings -> Repositories -> Ubuntu Software
Check "Installable from CD-ROM/DVD" and close
Reload (disregard connectivity errors)
Search for "bcmwl-kernel-source"
Right-click and mark for installation
Apply changes and reboot
Repeat steps 1.3 thru 1.4.2
From LiveUSB:
Navigate to pool -> main -> d -> dkms
Run "dkms_2.1.0.1-0ubuntu1_all.deb"
Navigate to pool -> restricted -> b -> bcmwl
Run "bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb"
Reboot
Repeat steps 2.1.6 thru 2.1.9 and 1.3 thru 1.4.2
Broadcom BCM4301/03/06/09 Hardware (B43 driver):
[B]NOTE: IF YOUR CARD IS A BCM4306 REV 2, OR ONLY HAS 802.11B CAPABILITY, IT USES
B43LEGACY. ALL OTHER MODELS USE B43. THE STEPS BELOW WILL BUILD BOTH B43 AND
B43LEGACY (AND GET FIRMWARE FOR BOTH TOO). THE KERNEL AUTOLOADER WILL
AUTOMATICALLY DO THE RIGHT THING AND LOAD THE CORRECT DRIVER FOR YOUR DEVICE.
ADDITIONAL INFO HERE. ASSUMES FRESH INSTALL. FOR LAPTOPS, ONCE THE SYSTEM REBOOTS
AFTER INSTALL, REBOOT AGAIN AND TOGGLE THE WIRELESS BUTTON (YES, IT COULD BE THAT
EASY).[/B]

Plug into the network via cable:
**IF WIRED CONNECTION WORKS:**
Open System -> Admin -> Update Manager
Check for updates, install, and reboot
After reboot, open System -> Admin -> Hardware Drivers
Look for "Broadcom B43 wireless driver";
**IF DRIVER IS PRESENT AND ACTIVATED:**
Remove network cable, toggle wireless button, and log into network.
**IF DRIVER IS PRESENT BUT NOT ACTIVATED:**
Activate and reboot;
After reboot, remove network cable, toggle wireless button, and log into network.
**IF DRIVER IS NOT PRESENT:**
Open System -> Admin -> Synaptic Pkg Mgr
Search for "b43-fwcutter" (if not available, move to step 2)
Right-click and mark for installation
Apply changes (answer yes when asked "Fetch and install firmware?")
Reboot
Repeat steps 1.3 thru 1.4.2
**IF WIRED CONNECTION DOES NOT WORK:**
From LiveCD (based on solution provided by jomtois here - edited for clarity):
Open Sytem -> Admin -> Synaptic Package Mgr
Ensure 9.10 LiveCD is in the drive
In Synaptic Package Mgr, open Settings -> Repositories -> Ubuntu Software
Check "Installable from CD-ROM/DVD" and close
Reload (disregard connectivity errors)
Search for "b43-fwcutter"
Right-click and mark for installation
Apply changes (answer yes when asked "Fetch and install firmware?")
Reboot
Repeat steps 1.3 thru 1.4.2
From LiveUSB:
Navigate to pool -> main -> d -> dkms
Run "dkms_2.1.0.1-0ubuntu1_all.deb"
Navigate to pool -> restricted -> b -> bcmwl
Run "bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb"
Reboot
Repeat steps 2.1.6 thru 2.1.9 and 1.3 thru 1.4.2
Transfer Files from Another Computer
[B]NOTE: IF NECESSARY, THE STA AND B43 PACKAGES CAN BE
DOWNLOADED USING THE LINKS BELOW. BE SURE TO INCLUDE THE
APPROPRIATE DEPENDENCIES.[/B]

STA Driver Source
[http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source)

B43 Driver Source
[http://packages.ubuntu.com/karmic/b43-fwcutter](http://packages.ubuntu.com/karmic/b43-fwcutter)

Cheers.

---

