---
title: "Why did my wireless just stop working?"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by MarkStarCrashes on 2009-12-13
I've been running 9.04 for a few months now with no connectivity problems. In fact my wireless connection was just fine up until about half an hour ago when it just stopped working. I am now plugged into a wired connection and all is fine but how can I figure out what went wrong with the wireless. When I click on the "Signal Bars icon" in the top right it doesn't even seem to see and possible wireless connections although my router is fine as my other craptop is getting a signal from it. It's just my machine that has suddenly stopped.

Please help.:confused:

---

### Post by The Toxic Mite on 2009-12-13
Hey!

Can you go to Applications > Accessories > Terminal, and do one of the following:


[LIST=1]
[*]If your wireless adaptor is integrated, can you post the output of the following commands: ```
lspci -v less, sudo lshw -c network, iwconfig
```
[*]In the case of a USB adaptor: ```
lsusb
```
[/LIST]
Thanks :)

---

### Post by MarkStarCrashes on 2009-12-13
Thanks for the quick reply. 

Somehow I don't think this is what you were looking for. Sorry see next post.

```
I are dumb.

```

---

### Post by MarkStarCrashes on 2009-12-13
Whoops. How about this...

```
markstar@markstar-laptop:~$ lspci -v 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, fast devsel, latency 0, IRQ 2299
    Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
    Memory at 80000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5110 [size=8]
    Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, fast devsel, latency 0
    Memory at 92500000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 50e0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 50c0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 50a0 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at 94705c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at 94700000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00003000-00004fff
    Memory behind bridge: 93700000-946fffff
    Prefetchable memory behind bridge: 0000000090400000-00000000914fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 92600000-936fffff
    Prefetchable memory behind bridge: 0000000091500000-00000000924fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 5080 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 5060 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 5040 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at 94705800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2301
    I/O ports at 5108 [size=8]
    I/O ports at 511c [size=4]
    I/O ports at 5100 [size=8]
    I/O ports at 5118 [size=4]
    I/O ports at 5020 [size=32]
    Memory at 94705000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: medium devsel, IRQ 11
    Memory at 94706000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 5000 [size=32]
    Kernel modules: i2c-i801

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: fast devsel, IRQ 11
    Memory at 94704000 (64-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 360b
    Flags: bus master, fast devsel, latency 0, IRQ 2300
    I/O ports at 3000 [size=256]
    Memory at 90410000 (64-bit, prefetchable) [size=4K]
    Memory at 90400000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at 90420000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
    Subsystem: Hewlett-Packard Company Device 137a
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at 92600000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k_pci
    Kernel modules: ath_pci, ath5k

```Then this ...```
sudo lshw -c network
```Said something so fast I couldn't read and returned to the input line.

And lastly... ```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```

---

### Post by The Toxic Mite on 2009-12-13
> **MarkStarCrashes said:**
> <snip>
[/code]Then this ...```
sudo lshw -c network
```Said something so fast I couldn't read and returned to the input line.


Would you be able to scroll back up?

---

### Post by MarkStarCrashes on 2009-12-13
> **The Toxic Mite said:**
> Would you be able to scroll back up?

Man, I'm having a bad brain day...

```
markstar@markstar-laptop:~$ sudo lshw -c network
[sudo] password for markstar: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:7a:78:2b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.101 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:69:5b:88:b3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:2d:fb:9a:a5:1b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
markstar@markstar-laptop:~$ 

```

---

### Post by MarkStarCrashes on 2009-12-13
For what it"s worth, I booted up Windows and while the blue light said the wireless card was activated, my machine still doesn't see any available networks in Windows either.





**Edited to add: i unplugged my machine and took the battery out and then put the battery back, plugged it back in, and viola! wireless card is back online...**

---

### Post by The Toxic Mite on 2009-12-14
> **MarkStarCrashes said:**
> 
**Edited to add: i unplugged my machine and took the battery out and then put the battery back, plugged it back in, and viola! wireless card is back online...**

Good! :)

---

