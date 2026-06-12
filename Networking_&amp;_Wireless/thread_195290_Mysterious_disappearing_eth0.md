---
title: "Mysterious disappearing eth0"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by mr_static on 2006-06-12
Hi forum,
first post, first fresh install of Dapper Drake so please bear with the newbieness.

The scenario: dual booting (for now) DD/WinXP on a machine with MSI KT4 mobo with onboard Broadcom NetXtreme BCM5702 Gigabit Ethernet Controller.  Using identical static LAN IP for this interface in both OS's.

The issue: on exiting XP and booting into Ubuntu, eth0 is gone. Rebooting into Ubuntu once again brings it back in good working order.

Troubleshooting so far - relevant entries in dmesg:

1) working eth0:

[4294693.858000] tg3.c:v3.47 (Dec 28, 2005)
[4294693.858000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 18 (level, low) -> IRQ 193
...
[4294694.078000] eth0: Tigon3 [partno(BCM95702A20) rev 1002 PHY(5703)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:10:dc:cc:76:b1
[4294694.078000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[4294694.078000] eth0: dma_rwctrl[763f0000]
...
[4294697.352000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[4294697.352000] tg3: eth0: Flow control is on for TX and on for RX.
...

2) eth0 not working:

[4294694.398000] tg3.c:v3.47 (Dec 28, 2005)
[4294694.398000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 18 (level, low) -> IRQ 193
...
[4294694.422000] tg3: Could not obtain valid ethernet address, aborting.
[4294694.422000] ACPI: PCI interrupt for device 0000:00:0f.0 disabled
[4294694.422000] tg3: probe of 0000:00:0f.0 failed with error -22
...

/etc/network/interfaces has:

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0


Conclusion so far: seems I could be facing an ACPI/PCI issue? I'm truly baffled as to why it only happens after having run XP.

My status: fairly clueless as to how to proceed from here. Hoping someone can help me suss this out, short of the obvious solution (ditching XP ;) ), which I'm not quite ready for. Any input greatly appreciated.

---

