---
title: "Network Connections Suddenly Stopped Working"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by mwhite1206 on 2010-03-29
Hi all,

I'm running an ASUS F3 laptop with dual boot Windows XP/Ubuntu 9.10. It's been working fine for almost a year now, but today I had a bad resume from closing my laptop, the screen lit up a bit but went nowhere for a while, so I restarted the computer via the hard switch. Now, it refuses to connect to ANY network, wired or wireless. It has the following problems:
- The Network Manager icon does not appear in the Notifications Panel anymore;
- When I try to open System > Preferences > Network Connections, nothing happens (as in, I click the thing, the menu closes but no Network Manager window appears);
- Plugging in an ethernet cable has no effect, and I can't get internet, even without any of the network manager icons.
It's almost as if network-manager has exploded, died, and refuses to be resurrected. The various restart network-manager commands I've found on here seem to do nothing, and I can't see a network-manager process in my System Monitor.

I've tried doing stuff like nm-applet --ns-disable or whatever the command is (I can't be bothered running off and finding a post to make sure that's right.) I've also tried adding a Network Monitor thing to my Notifications Area, but it only shows info, and doesn't give me the option to make, edit, or even see what connections are available. And, obviously, I've tried rebooting, and making sure the network card is still switched on (to the best of my knowledge using the hard switch on the front of the computer.)

Here's some outputs for you:

```
sudo lshw -C network
[sudo] password for marc: 
  *-network DISABLED      
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:1f:c6:13:8f:8a
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:18 memory:fdcc0000-fdcfffff memory:fdca0000-fdcbffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:15:af:7e:3a:a0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.55+,07/26/2007,5.3.0.67 latency=0 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:fe5f0000-fe5fffff
```

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
03:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
08:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
```

```
sudo ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:667 (667.0 B)  TX bytes:667 (667.0 B)


sudo iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I noted that in the output of lshw -C network, the devices are labelled as DISABLED - this seems to be the case most of the time, but even if that DISABLED doesnt appear, nothing changes. The driver I had running for the Atheros card no longer shows up in System > Administration > Hardware Drivers, but ndiswrapper still shows it as being there:

```

ndiswrapper -l
net5210b : driver installed
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath5k)
```

I also noticed something odd when I tried the nm-applet command (the original time I did it I had the right option in there, this is just as an example):
```
marc@juju:~$ nm-applet 
nm-applet: error while loading shared libraries: /usr/lib/libnm-util.so.1: unsupported version 0 of Verneed record
```

A lot of the related things I've found on here so far have to do with people who've managed to accidentally delete Network Manager, or those who need to massage their Atheros wireless to make it work (but still get wired connections) - obviously, not my problem. Any ideas?

---

### Post by mwhite1206 on 2010-03-29
I forgot to mention, the hardware seems fine, networking (of both sorts) works just fine in Windows.

---

### Post by mwhite1206 on 2010-03-29
Issue solved - I worked out that my libnm-util1 package had somehow become mangled. I downloaded the .deb package file onto a USB stick, installed it on my Linux machine, rebooted, and everything (networking + not waking up from suspend) was fixed.

---

### Post by Iowan on 2010-03-29
Glad you found it - mark this one [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")!

---

