---
title: "BCM4313 not responding on Natty 11.04 Please Help"
date: 2011-11-10
forum: Networking &amp; Wireless
---

### Post by skizzikskizziks on 2011-11-10
Hi, I'm looking for some help.

I'm running Ubuntu 11.04, dualbooting Windows 7 and have had intermittent wireless problems. Occasionally I boot up, and my wireless card doesn't work at all. It doesn't show a list of available networks even when I'm in a zone where there definitely are networks. Sometimes this happens, and sometimes it doesn't. Rebooting usually works (i.e. the wireless card works after I reboot) But this time it didn't. I've rebooted in Windows 7 as well as shutting down and restarting without rebooting in Windows 7. 

The last major process I performed in Ubuntu were sudo apt-get update, and sudo apt-get upgrade. The present wireless failure occurred the next time I booted up in Natty Narwhal after updating/upgrading. 

I ran @Terminal: "sudo lspci -v" and got these results:

03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
Subsystem: Dell Device 0010
Flags: bus master, fast devsel, latency 0, IRQ 10
Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [40] Power Management version 3
Capabilities: [58] Vendor Specific Information: Len=78 <?>
Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
Capabilities: [d0] Express Endpoint, MSI 00
Capabilities: [100] Advanced Error Reporting
Capabilities: [13c] Virtual Channel
Capabilities: [160] Device Serial Number [omitted]
Capabilities: [16c] Power Budgeting <?>
Kernel modules: brcm80211


I ran @Terminal: sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c1
       serial: b8:ac:6f:70:f7:a2
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.5.142 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:f0400000-f043ffff ioport:2000(size=128)

I also attempted to engage the built-in driver by going to "system settings" -> "additional drivers", but it would not activate the driver. It told me to check the log for details, but for some reason I couldn't access the log (which I don't know anything about). NB I have the administrative account. I also don't know that much about Ubuntu, so I may be making elementary mistakes. 

I'd really appreciate any help solving this problem, as I need my wireless card/drivers to be reliable for my at-home and on-the-go work of various kinds. NB: I tend to access public wireless in various places, in case the networks I'm on matter somehow. 

Thanks!

---

### Post by drs305 on 2011-11-10
skizzikskizziks,

Welcome to the Ubuntu Forums!

Have you seen the 'sticky' thread in the Networking forum? 

The title states Oneiric but subtitle says it applies to 11.04 as well:
[http://ubuntuforums.org/showthread.php?t=1604868]("http://ubuntuforums.org/showthread.php?t=1604868")

---

### Post by skizzikskizziks on 2011-11-10
I tried all the options on that link, and they didn't work for me.

Solution 1.  I was unable to install the STA through 'Additional Drivers' it returned 'sorry, the installation of this driver failed'.

Solution 2.  I reinstalled the bcmwl-kernel-source package as they instructed, and then tried to run the next step and got this:

@Terminal:sudo modprobe -r b43 ssb wl 
FATAL: Module wl not found.

@Terminal:sudo modprobe wl
FATAL: Module wl not found.

Is that Module a component of the bcmwl-kernel-source package that's somehow missing?

Solution 3.  I used the second option to install firmware-b43-lpphy-installer, but it told me that the exit process had returned an error, the details of which are below:

(Reading database ... 181097 files and directories currently installed.)
Removing firmware-b43-installer ...
Deleting old extracted firmware...
Selecting previously deselected package firmware-b43-lpphy-installer.
(Reading database ... 181094 files and directories currently installed.)
Unpacking firmware-b43-lpphy-installer (from .../firmware-b43-lpphy-installer_4.174.64.19-5_all.deb) ...
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:4727)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:4727)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer


I may just be failing to do this right, but I have followed the instructions of those three solutions, and they all come up with errors, so I hypothesize that something is missing that ought to be there. I've been looking for solutions on different threads for a couple of days, but nothing seems to fix it. Anyone have further ideas?

---

### Post by bkratz on 2011-11-11
Did you see this one?

[http://ubuntuforums.org/showthread.php?t=1783272](http://ubuntuforums.org/showthread.php?t=1783272)

---

### Post by jskandhari on 2011-11-14
Mine wasn't working I followed these steps on Ubuntu 11.10 [http://ubuntuforums.org/showthread.php?t=1879096](http://ubuntuforums.org/showthread.php?t=1879096)

---

