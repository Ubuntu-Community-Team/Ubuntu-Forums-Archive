---
title: "Can't enable wireless adaptor"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by newb85 on 2009-05-18
I just did a fresh install of Jaunty.

The wireless adapter, which is enabled and functional in Windows, is listed as "DISABLED" by the lshw command in Ubuntu.

The only thing Ubuntu help says to do in this case is enable the adapter in Windows, which is worthless advice, since that is already done.

I'm running Compaq Presario desktop with an internal Linksys 802.11g card.

How can I fix this?

---

### Post by superprash2003 on 2009-05-19
in your ubuntu terminal type **lshw -C network** and post output here

---

### Post by newb85 on 2009-05-19
Here's the output:

  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1 DISABLED
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:11:2f:1c:12:a4
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no 

maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:e5:9c:dd:b8
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 16:9f:c0:a2:f3:f6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by ixifx on 2009-05-19
are you using a laptop?

---

### Post by newb85 on 2009-05-19
It's a desktop.

---

### Post by timcredible on 2009-05-19
you could install ndisgtk via synaptic (system->administration->synaptic), then run that program (system->administration->windows wireless), and just point to your windows wireless driver .inf file.  then reboot, should take care of it.

---

### Post by newb85 on 2009-05-19
Is there a way to download ndisgtk using Windows and then install it in Ubuntu?  Without wireless, I have not internet, and so using Synaptic to install is not an option.

---

### Post by ixifx on 2009-05-19
if you have a usb disk you can get files from the repository, which is what I've been doing.

---

### Post by newb85 on 2009-05-19
I downloaded ndisgtk from ubuntu.com.  When I went to install it, Ubuntu wouldn't install it because of dependency issues.

---

### Post by newb85 on 2009-05-19
Okay, I have ndisgtk installed and running.  (Wrapper files...it will be so nice to use Synaptic again...)

How do I find the windows wireless driver, though?

---

### Post by newb85 on 2009-05-19
Okay, I now have ndisgtk pointed to the Windows wireless drivers.  The program's response is that the hardware is not present (even after reboot).  Arg!  Help?  Someone?

---

