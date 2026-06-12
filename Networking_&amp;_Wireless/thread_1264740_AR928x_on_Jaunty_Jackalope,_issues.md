---
title: "AR928x on Jaunty Jackalope, issues"
date: 2009-09-12
forum: Networking &amp; Wireless
---

### Post by Pastafarious on 2009-09-12
Hello, I have been scouring the forums trying to find a solution to my lack of wireless network connectivity problem.  Currently I am running Ubuntu 9.04 on an ASUS g50v.  The network card is:
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Device 1a3b:1067
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fdff0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k
Any help would be greatly appreciated

---

### Post by walt.smith1960 on 2009-09-13
Two possibilities.

One is to find a USB WiFi adapter that is recognized. I used a TrendNet UB424(? I think) version 3.1. Once you are able to connect, install the linux backports. The procedure is documented in this forum. The other choice is to use the Karmic Alpha release.I'm running an Eee1005HA. I have gone this route because Karmic supports wired & wireless networking 'out of the box', and the wifi switch (fn+f2) work in Karmic NBR. The only problem I've had with Karmic is wifi connections dropping after resuming a suspended machine. A restart clears the connection problem but it IS an alpha release so I didn't expect perfection.

---

