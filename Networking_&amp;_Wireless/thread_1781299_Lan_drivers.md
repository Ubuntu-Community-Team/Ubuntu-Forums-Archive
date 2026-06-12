---
title: "Lan drivers"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by Th3_1_&amp;_o/|/LY on 2011-06-13
HI,

UBUNTU NEWBIE HERE!! So, I'm a total beginner.

Having just Installed Ubuntu 11.4, I require LAN drivers for ASUS A8N5X Motherboard. Where can I get the drivers? And instructions on how to install them. All  help is much appreciated.

Many thanks!

---

### Post by StrayEddy on 2011-06-13
Open a terminal (Ctrl+Alt+T)

Then type: 
lspci -v | less

Post the result Here

---

### Post by Th3_1_&amp;_o/|/LY on 2011-06-13
Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp
Here's the list: 

00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0000000-d1ffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport
        Kernel modules: shpchp

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Kernel driver in use: k8temp
        Kernel modules: k8temp

01:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent] (prog-if 00 [VGA controller])
        Subsystem: PC Partner Limited Device 1490
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        I/O ports at a000 [size=256]
        Memory at d1000000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at d0000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: radeon
        Kernel modules: radeon, radeonfb

01:00.1 Display controller: ATI Technologies Inc RV370 secondary [Sapphire X550 Silent]
        Subsystem: PC Partner Limited Device 1491
        Flags: fast devsel
        Memory at d1010000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>

05:07.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 04) (prog-if 10 [OHCI])
        Subsystem: Agere Systems FW322/323
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at d2000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: firewire_ohci
        Kernel modules: firewire-ohci

(END)

---

### Post by StrayEddy on 2011-06-13
I don't see your network chip information.

Could you post:
lspci | [COLOR=Black]grep [/COLOR]-i wireless

or

lspci | grep -i Ethernet

or

lspci

---

### Post by Th3_1_&amp;_o/|/LY on 2011-06-13
theone@theone-System-Product-Name:~$ lspci | grep -i Ethernet
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
theone@theone-System-Product-Name:~$

---

### Post by StrayEddy on 2011-06-13
Your card is supported by Forcedeth drivers, wich are normally included by default in the kernel.

Try the solution of this post:

[http://ubuntuforums.org/showthread.php?t=211823](http://ubuntuforums.org/showthread.php?t=211823)

---

### Post by Th3_1_&amp;_o/|/LY on 2011-06-13
Eddy, many thanks for your help!

---

### Post by StrayEddy on 2011-06-13
Np, but is it my last post that fixed your problem?

If it isn't then please share with us your solution.

Thank you.

---

