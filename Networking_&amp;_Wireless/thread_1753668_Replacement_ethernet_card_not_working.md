---
title: "Replacement ethernet card not working"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by ephemerian on 2011-05-09
The on-board NIC on my machine died this morning, so I've just gone out and bought a replacement PCI card. The card has been recognised by Karmic, but it's not working. /var/log/messages says:

    ```
May  9 11:21:58 ian-desktop kernel: [    2.082324] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
May  9 11:21:58 ian-desktop kernel: [    2.082334] r8169 0000:04:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
May  9 11:21:58 ian-desktop kernel: [    2.082355] r8169 0000:04:02.0: (unregistered net_device): no PCI Express capability
May  9 11:21:58 ian-desktop kernel: [    2.082665] r8169 0000:04:02.0: eth0:     RTL8169sb/8110sb at 0xffffc90000c70000, 00:11:3b:15:41:1b, XID 10000000 IRQ 18
May  9 11:21:58 ian-desktop kernel: [   11.103825] r8169 0000:04:02.0: eth1: link down
May  9 11:22:47 ian-desktop kernel: [   60.240622] r8169 0000:04:02.0: eth1: link down
May  9 11:27:15 ian-desktop kernel: [  327.690765] r8169 0000:04:02.0: eth1: link down
May  9 11:27:46 ian-desktop kernel: [  358.512287] r8169 0000:04:02.0: eth1: link down

```I'm guessing that I don't have a driver for the r8169 card. There is a linux driver on the install disk that came with the card (Micronet SP2612R) but it won't compile when I try to make it.

Any suggestions for how I install the appropriate driver (noting that I have to sneakernet files across via usb stick), or any other diagnostics I should try?

Thanks,
Ian

---

### Post by ephemerian on 2011-05-09
Sorry, used the wrong tag - this is on Karmic 10.10, not Lucid

---

### Post by ephemerian on 2011-05-09
Oh dear, how embarrassing. PEBCK ... ethernet cable not yet in new NIC's ethernet port. Doh!

---

