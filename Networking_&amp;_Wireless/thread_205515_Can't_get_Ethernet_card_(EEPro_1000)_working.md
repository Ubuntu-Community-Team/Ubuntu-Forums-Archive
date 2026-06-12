---
title: "Can't get Ethernet card (EEPro 1000) working"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by HankB on 2006-06-28
I've just replaced the ethernet card in my desktop with an Intel EtherExpress Pro gigabit card. lspci shows:
```
0000:00:09.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
        Subsystem: Intel Corporation PRO/1000 MT Desktop Adapter
        Flags: 66MHz, medium devsel, IRQ 193
        Memory at fb020000 (32-bit, non-prefetchable) [size=128K]
        Memory at fb040000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at b400 [size=64]
        Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 2
        Capabilities: [e4] PCI-X non-bridge device.
        Capabilities: [f0] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
```

Inserting the e1000 module shows (from dmesg)
```
[17180517.432000] Intel(R) PRO/1000 Network Driver - version 7.0.33-k2
[17180517.432000] Copyright (c) 1999-2005 Intel Corporation.
[17180517.432000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 193
[17180517.688000] e1000: 0000:00:09.0: e1000_probe: (PCI:33MHz:32-bit) 00:07:e9:0c:fe:10
[17180517.724000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
```

And trying to bring it up gets:
```
root@toonsinator:/var/log# ifconfig eth0
eth0: error fetching interface information: Device not found
root@toonsinator:/var/log#
```
There are no additional hints from dmesg.

Is there something I can try to get thus working? Prior to this I had another card I had used for some time and had just recently switched to the VIA interface on the motherboard. Early this morning we had an electrical storm with some close lightening hits. I found 2 of 4 ports on my gigabit switch dead and another computer unable to connect to the LAN. Now the motherboard connection on this PC remains dark when I connect to a known working port on the switch. The PCI card interface (which I just replaced) would not light the FDX LED on the hub but was otherwise detected. It would not otherwise connect.

The card I have there now was sitting on a shelf so I believe it is OK. I'm wondering if there is an alternate driver to try or something else I'm overlooking or if there is possible MOBO damage.

thanks,
hank

---

### Post by HankB on 2006-06-28
Well, that card seems to be identified as eth2 even though dmesg shows it as eth0. So I have that one working now.

I wonder how these get assigned and reassigned.

thanks,
hank

---

