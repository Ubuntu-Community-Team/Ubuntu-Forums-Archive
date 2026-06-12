---
title: "Trouble with Linksys PCI wireless card"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by mnew on 2009-09-06
Hi,
I've gone through the forums here and have tried several things to get my old PC to connect to my unsecured wireless network without success and am hoping some generous soul can help me.  
Card: Linksys WMP 11 Wireless PCI 
PC: Compaq Presario Model 5BW135
OS: ubuntu 9.04

I am able to connect to the wireless network from a separate computer.  From the forums, here's what I've garnered is useful info:

Various GUI info:
===============
"Enable Networking" and "Enable Wireless" selected, "Wireless networks" greyed out, "Device not managed" greyed out.
Wireless connection added using the "Edit Connections" dialog, SSID=tRadEwinds621, Mode=Infrastructure, Security=None, Connect automatically=checked, Available to all users=checked
"System > Administration > Hardware Drivers" lists nothing and says "No proprietary drivers are in use on this system".

Contents of /etc/network/interfaces file:
===========================
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid tRadEwinds621
===========================

Result of iwconfig command:
===========================
ginny@ginny-desktop:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"tRadEwinds621"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
===========================

Result of ifup -v wlan0:
===============
ginny@ginny-desktop:~$ sudo ifup -v wlan0
[sudo] password for ginny: 
ifup: interface wlan0 already configured
===============

Result of lspci -vnn (abbreviated):
 ===========================
ginny@ginny-desktop:~$ sudo lspci -vnn
[sudo] password for ginny: 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801AA PCI Bridge [8086:2418] (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 40000000-400fffff
    Kernel modules: shpchp


01:0b.0 Network controller [0280]: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller [14e4:4301] (rev 02)
    Subsystem: Linksys Device [1737:4301]
    Flags: bus master, fast devsel, latency 66, IRQ 11
    Memory at 40000000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
 ===========================

Thanks in advance!

---

### Post by Cuba71 on 2009-09-07
Ubuntu is assigning b43-pci-bridge driver to handle this card.
There're several versions of Linksys WMP 11 wireless adapters, each one with a different Vendor/Product ID.
You need to find out wich version do you have, and if Ubuntu's native driver will do the job or you may have to install a Windows driver using ndiswrapper

---

### Post by mnew on 2009-09-07
Thank you for the reply.  I pulled the card and the following are the information I could find printed on it:
Model No.:WMP11
FCC ID: PKW-WMP11-V27
IC: 3839A-WMP11
Serial No.: BB7272B86884
I do have Windows drivers for it and was able to get it working without too much difficulty under Windows 98. I will scrounge around the ubuntu documentation and the WWW at large to see what I can find and report my results.

---

### Post by Cuba71 on 2009-09-08
Check this site for more information on b43 drivers and devices supported

[http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")

---

### Post by t0mppa on 2009-09-08
The link Cuba71 provided should indeed have all the info you need. As you can see the [14e4:4301] is listed as supported.

The thing with b43 (and b43legacy in your case) is that it relies on using firmware (software installed directly to your wireless card, not to the Linux file system) installed through an application called b43-fwcutter. Since this firmware isn't open source, it is not installed automatically when you install Ubuntu and thus the driver doesn't work out of the box. But once you have the firmware installed, everything should go smoothly.

---

