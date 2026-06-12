---
title: "Satellite 305d 8.04 ubuntu"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by mgoblue on 2009-01-06
Hi, I have a toshiba satellite 305d 4830.  I cannot get internet to work at all on it, wireless or ethernet.  I am using the 64 bit 8.04 ubuntu.  Can anyone provide assistance?

EDIT: Ethernet solved, wireless still isn't D=

---

### Post by cdtech on 2009-01-06
Can you see the interface using the command:
```
ifconfig
```
How is your /etc/network/interfaces configured?

---

### Post by semi_fiction on 2009-01-06
Check out this link, the L305D has the same network hardware as the L305, which is the laptop I own.
[http://swinky-linuxblog.blogspot.com/2008/11/ubuntu-on-toshiba-satellite-l305-howto.html]("http://swinky-linuxblog.blogspot.com/2008/11/ubuntu-on-toshiba-satellite-l305-howto.html")

---

### Post by mgoblue on 2009-01-06
> **cdtech said:**
> Can you see the interface using the command:
```
ifconfig
```
How is your /etc/network/interfaces configured?

output of ifconfig is (i'm hand typing this, so spacing will be off..): 

```
lo       link encap:Local Loopback
   inet addr:127.0.0.1 Mask:255.0.0.0
   inet6 addr: ::1/128 Scope:host
   UP LOOPBACK RUNNING MTU:16436 Metric:1
   RX packets:1656 errors:0 dropped:0 overruns:0 frame:0
   TX packets:1656 errors:0 dropped:0 overruns:0 carrier:0
   collisions:0 txqueuelen:0
   RX bytes:82800 (80.8 kb) TX bytes:82800 (80.8 kb)
   


```

/etc/network/interfaces  is as:

```
 auto lo
iface lo inet loopback
```

---

### Post by cdtech on 2009-01-06
When the interface doesn't appear in "ifconfig" and the hardware appears in lspci, this means that no driver is claiming the hardware. Use the command "lspci" to see if the hardware is detected. From there we can see if the correct driver is being loaded.

---

### Post by mgoblue on 2009-01-06
> **cdtech said:**
> When the interface doesn't appear in "ifconfig" and the hardware appears in lspci, this means that no driver is claiming the hardware. Use the command "lspci" to see if the hardware is detected. From there we can see if the correct driver is being loaded.

lspci gives:

```

:~/Desktop$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Toshiba America Info Systems Unknown device 9602
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4355 (rev 12)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
09:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
09:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)


```

---

### Post by cdtech on 2009-01-06
There looks to be a bug to this issue with the Marvell and the driver sky2.ko. Type the command:
```
modinfo sky2
```
and lets see if it's listed within the module.

---

### Post by mgoblue on 2009-01-06
```
filename:       /lib/modules/2.6.24-19-generic/kernel/drivers/net/sky2.ko
version:        1.20
license:        GPL
author:         Stephen Hemminger <shemminger@linux-foundation.org>
description:    Marvell Yukon 2 Gigabit Ethernet driver
srcversion:     3C92CA5C9DF88F503D683D7
alias:          pci:v000011ABd0000436Csv*sd*bc*sc*i*
alias:          pci:v000011ABd0000436Bsv*sd*bc*sc*i*
alias:          pci:v000011ABd0000436Asv*sd*bc*sc*i*
alias:          pci:v000011ABd00004369sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004368sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004367sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004366sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004365sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004364sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004363sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004362sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004361sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004360sv*sd*bc*sc*i*
alias:          pci:v000011ABd0000435Asv*sd*bc*sc*i*
alias:          pci:v000011ABd00004357sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004356sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004354sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004353sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004352sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004351sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004350sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004347sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004346sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004345sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004344sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004343sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004342sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004341sv*sd*bc*sc*i*
alias:          pci:v000011ABd00004340sv*sd*bc*sc*i*
alias:          pci:v00001186d00004B03sv*sd*bc*sc*i*
alias:          pci:v00001186d00004B02sv*sd*bc*sc*i*
alias:          pci:v00001186d00004001sv*sd*bc*sc*i*
alias:          pci:v00001186d00004B00sv*sd*bc*sc*i*
alias:          pci:v00001148d00009E00sv*sd*bc*sc*i*
alias:          pci:v00001148d00009000sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.24-19-generic SMP mod_unload 
parm:           debug:Debug level (0=none,...,16=all) (int)
parm:           copybreak:Receive copy threshold (int)
parm:           disable_msi:Disable Message Signaled Interrupt (MSI) (int)


```

---

### Post by cdtech on 2009-01-06
The ID (4355) is not listed within the driver.
Here's how to patch the driver:
```
sudo su (become root)
```
```

rmmod sky2
cd /lib/modules/`uname -r`/kernel/drivers/net
cp -p sky2.ko{,.orig}
perl -pe 's/\0\0\x6c\x43/\0\0\x55\x43/g' sky2.ko.orig > sky2.ko

```

Run modprobe sky2. You can check the "dmesg" to see if the device is detected.
After reboot you should have Ethernet. Use "ifconfig" to verify (eth0).

---

### Post by mgoblue on 2009-01-06
Thank you so much, I know have ethernet. Does anyone know how to get the wireless working now?

---

### Post by peterwil on 2009-06-05
Try madwifi... I have used this for over 6 months on a Toshiba Satellite L305D -S5881 on AMD64bit on a 8.0.4 64bit version and it works very well. 
I was on ndiswrapper which would connect but without security and  then came across the madwifi post.. :-)

Just reinstalled Ubuntu Jaunty and it still works.

Please see the howto and pin a medal on the guy who wrote it..(aandu ).. :-)

Cheers
Peter

---

