---
title: "Edimax EW-7711ln recognized but cannot connect"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by Dragon Lord on 2011-01-25
Hi,
I'm new to Linux and using xubuntu.

I have two PCI network cards:
    Wired - Successfully connects to the internet and removed from the outputs describes below.
    Wireless - A new and works well in WinXP - Edimax EW-7711ln: problematic - can't connect. Manufacture says it's supported in Linux.
    Although in it's site it doesn't have any linux driver to download. The XP driver contain 2 .cab files that cannot be accessed using unshield/cabextract so I guess "ndiswrapper" is not an option.

Other Linux disrtos also didn't recognize the wireless as well.
Below I added as much information as I could get. Please tell me if you need anything else.
Please help me avoid reinstalling Windows XP:)
Thanks in advanced.


sudo iwlist wlan0 scan
wlan0     No scan results
========================================================================
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
========================================================================
 sudo lspci | grep Network
00:10.0 Network controller: RaLink Device 3060
========================================================================
sudo lshw -c network
  *-network:1
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 10
       bus info: pci@0000:00:10.0
       logical name: wlan0
       version: 00
       serial: 00:1f:1f:a6:60:a4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-24-generic firmware=N/A latency=64 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:3 memory:dffe0000-dffeffff
========================================================================
nm-tool

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        00:1F:1F:A6:60:A4

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
========================================================================
sudo lshw -businfo | grep network
pci@0000:00:0f.0  eth0        network     21x4x DEC-Tulip compatible 10/100 Ethernet
pci@0000:00:10.0  wlan0       network     RaLink
========================================================================
lspci -v
00:10.0 Network controller: RaLink Device 3060
    Subsystem: Edimax Computer Co. Device 7711
    Flags: bus master, slow devsel, latency 64, IRQ 3
    Memory at dffe0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci

---

### Post by Dragon Lord on 2011-01-26
Thanks for all the replies:)

Problem solved:
Use ndiswrapper with the driver posted here:
[http://ubuntuforums.org/showthread.php?t=1615304&highlight=ew-7711ln&page=4](http://ubuntuforums.org/showthread.php?t=1615304&highlight=ew-7711ln&page=4)

Make sure u r using the file: rt2860.zip

---

