---
title: "Unable to activate PCI-X Quad port NIC"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by sidj8 on 2009-08-14
lspci shows the quad port nic card is detected but has no memory assigned , and the status is disabled. Im not sure i need to change any settings in the bios or recompile the kernel again to include support for PCI-X devices. 

[I]04:04.0 Ethernet controller: Intel Corporation 82546GB PRO/1000 GT Quad Port Server Adapter (rev 03)
        Subsystem: Intel Corporation Unknown device 1199
        Flags: bus master, 66MHz, medium devsel, latency 52, IRQ 58
        Memory at <unassigned> (64-bit, non-prefetchable) [disabled]
        I/O ports at 4000 [size=64]
        Capabilities: [dc] Power Management version 2
        Capabilities: [e4] PCI-X non-bridge device
        Capabilities: [f0] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

04:04.1 Ethernet controller: Intel Corporation 82546GB PRO/1000 GT Quad Port Server Adapter (rev 03)
        Subsystem: Intel Corporation Unknown device 1199
        Flags: bus master, 66MHz, medium devsel, latency 52, IRQ 66
        Memory at <unassigned> (64-bit, non-prefetchable) [disabled]
        I/O ports at 4040 [size=64]
        Capabilities: [dc] Power Management version 2
        Capabilities: [e4] PCI-X non-bridge device
        Capabilities: [f0] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

04:06.0 Ethernet controller: Intel Corporation 82546GB PRO/1000 GT Quad Port Server Adapter (rev 03)
        Subsystem: Intel Corporation Unknown device 1199
        Flags: bus master, 66MHz, medium devsel, latency 52, IRQ 74
        Memory at <unassigned> (64-bit, non-prefetchable) [disabled]
        I/O ports at 4080 [size=64]
        Capabilities: [dc] Power Management version 2
        Capabilities: [e4] PCI-X non-bridge device
        Capabilities: [f0] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-

04:06.1 Ethernet controller: Intel Corporation 82546GB PRO/1000 GT Quad Port Server Adapter (rev 03)
        Subsystem: Intel Corporation Unknown device 1199
        Flags: bus master, 66MHz, medium devsel, latency 52, IRQ 82
        Memory at <unassigned> (64-bit, non-prefetchable) [disabled]
        I/O ports at 40c0 [size=64]
        Capabilities: [dc] Power Management version 2
        Capabilities: [e4] PCI-X non-bridge device
        Capabilities: [f0] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-[/I]

---

