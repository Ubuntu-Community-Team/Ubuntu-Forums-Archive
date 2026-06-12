---
title: "Fresh Install of 9.10, no more wireless. (Dell Latitude e6500)"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by Andante on 2009-10-26
Hey everyone,

I decided to do a fresh install of Ubuntu with 9.10. Before that I had used Jaunty and Intrepid with no problem with my wireless on this same laptop, but now all of a sudden I have no support. I was told to install WICD so I did that, but I see no change. It always worked with no configuration for me before so I&#7743; at a loss for what to do.

Here's some info that may or may not be helpful:

sudo lshw -C network
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:21:70:a9:4e:55
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=half firmware=1.7-7 ip=140.180.189.163 latency=0 link=yes multicast=yes port=twisted pair speed=10MB/s
       resources: irq:30 memory:f6fe0000-f6ffffff memory:f6fdb000-f6fdbfff ioport:efe0(size=32)
  *-network
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f1ffc000-f1ffffff



sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



sudo lspci -k
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Kernel modules: intel-agp
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
    Kernel driver in use: e1000e
    Kernel modules: e1000e
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Kernel driver in use: uhci_hcd
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Kernel driver in use: uhci_hcd
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Kernel driver in use: uhci_hcd
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
    Kernel modules: iTCO_wdt
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 03)
    Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Kernel modules: i2c-i801
01:00.0 VGA compatible controller: nVidia Corporation G98M [Quadro NVS 160M] (rev a1)
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb


thanks!

EDIT: I just tried to install a driver I found from the Broadcom site using this readme [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

but I couldn't remove ssb and b43 like it said I had to:

rmmod b43
ERROR: Removing 'b43': Operation not permitted

rmmod ssb
ERROR: Module ssb is in use by b43

Any ideas?

---

### Post by Andante on 2009-10-26
All I had to do was change the instructions to sudo modprobe -r instead of rmmod and it now works fine!

---

### Post by bparman on 2009-12-02
Thanks for posting,   this worked for me also.

---

### Post by bones16v on 2009-12-02
I have the same problem how do I change that?

---

### Post by ump001 on 2009-12-20
hi,

Smack this into your terminal and you should be ok hopefully:

sudo modprobe -r b44 ssb wl
sudo modprobe ieee80211_crypt_tkip 
sudo modprobe  wl
sudo modprobe b44
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...

---

### Post by ad4msmack on 2010-01-18
Great. Worked! I just smack the command into the terminal and all of the sudden I had wireless. 
Thanks

---

### Post by don2u on 2010-03-08
Didn't work for me.

After
sudo modprobe -r b44 ssb wl

I get
FATAL: Module ssb is in use.

---

### Post by bkratz on 2010-03-08
> **don2u said:**
> Didn't work for me.

After
sudo modprobe -r b44 ssb wl

I get
FATAL: Module ssb is in use.

If your machine uses a Broadcom device for the ethernet controller (not the wireless)  I believe it need the ssb file. If you look at 

lspci

(LSPCI in the terminal) Applications>>Accessories>>Terminal
What does it show for your network and also ethernet controller. You can just copy/paste them here.

---

### Post by don2u on 2010-03-08
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Here they are.

---

### Post by don2u on 2010-03-08
This thread solved my issue:
[http://ubuntuforums.org/showthread.php?p=8914296](http://ubuntuforums.org/showthread.php?p=8914296)

For me, there was another Broadcom driver listed (B43) that didn't work. The STA driver works great!

Thanks.

---

