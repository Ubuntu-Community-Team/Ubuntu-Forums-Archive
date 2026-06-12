---
title: "eth0 not working on via EPIA board"
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by Rounan on 2006-07-15
Hi,

I just migrated a system from debian unstable to xubuntu in order to get a webcam working - and the webcam does work! However, my LAN connection stopped working. It works just fine in the debian install, but pings to local machines fail in xubuntu. the /etc/network/interfaces files are identical in each install, so I think it has to be a difference in the kernel. the debian system uses 2.6.7, while the xubuntu one uses... whatever came on the 6.06 LTS cd. I haven't been able to update it because internet is broken. ;)

Here are the relevant lines from /var/log/messages:

Debian system:

```
Oct 26 13:56:09 ROBOT1 kernel: NET: Registered protocol family 23
Oct 26 13:56:09 ROBOT1 kernel: via-rhine.c:v1.10-LK1.1.20-2.6 May-23-2004 Written by Donald Becker
Oct 26 13:56:09 ROBOT1 kernel: eth0: VIA VT6105 Rhine-III at 0xd000, 00:40:63:c9:a2:b5, IRQ 11.
Oct 26 13:56:09 ROBOT1 kernel: eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 0081.
Oct 26 13:56:09 ROBOT1 kernel: eth1: VIA VT6102 Rhine-II at 0xe800, 00:40:63:c9:a2:b4, IRQ 11.
Oct 26 13:56:09 ROBOT1 kernel: eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
```

Xubuntu system:

```
Jul 15 20:49:34 localhost kernel: [4294700.552000] NET: Registered protocol family 23
Jul 15 20:49:34 localhost kernel: [4294700.941000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
Jul 15 20:49:34 localhost kernel: [4294700.942000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Jul 15 20:49:34 localhost kernel: [4294700.942000] PCI: Via IRQ fixup for 0000:00:0f.0, from 9 to 11
Jul 15 20:49:34 localhost kernel: [4294700.947000] eth0: VIA Rhine III at 0x1d000, 00:40:63:c9:a2:b5, IRQ 11.
Jul 15 20:49:34 localhost kernel: [4294700.948000] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 0081.
Jul 15 20:49:34 localhost kernel: [4294700.948000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul 15 20:49:34 localhost kernel: [4294700.955000] eth1: VIA Rhine II at 0x1e800, 00:40:63:c9:a2:b4, IRQ 11.
Jul 15 20:49:34 localhost kernel: [4294700.956000] eth1: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
```

So in the Xubuntu system, there's some extra IRQ magic going on...

On both systems, lsmod shows the via_rhine module loaded, making use of the mii module.

Please let me know if you have any ideas!

Thanks,
Rounan

---

