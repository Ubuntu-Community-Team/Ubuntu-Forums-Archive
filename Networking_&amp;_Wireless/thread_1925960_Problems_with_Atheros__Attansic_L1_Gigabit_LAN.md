---
title: "Problems with Atheros / Attansic L1 Gigabit LAN"
date: 2012-02-15
forum: Networking &amp; Wireless
---

### Post by jmprince80 on 2012-02-15
Hi, 

I'm using an asustek P5KPL-VM motherboard which has the above mentioned NIC chip onboard.

Using the windows XP driver (under XP) the NIC is working fine.

However, using ubuntu (11.04 and 11.10) there seems to be a problem, I initially thought that this might have been a problem relating to the new 3.x line of kernels, but the results are the same regardless of kernel variant.

Some outputs:

```

$ dmesg | grep atl1

[    1.128529] atl1 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.128544] atl1 0000:02:00.0: setting latency timer to 64
[    1.128611] atl1 0000:02:00.0: version 2.1.3
[    1.224245] atl1 0000:02:00.0: PCI INT A disabled
[    1.224257] atl1: probe of 0000:02:00.0 failed with error -5

$ lspci -vvnn

02:00.0 Ethernet controller [0200]: Atheros Communications L1 Gigabit Ethernet [1969:1048] (rev ff) (prog-if ff)
	!!! Unknown header type 7f
	Kernel modules: atl1

```

Wondering if this is related to how linux handles PCI interrupts?

If anyone could shed some light on this would be much appreciated!

Thanks

Jamie

---

### Post by chili555 on 2012-02-15
How are the interrupts set up in your BIOS? I have the best performance from 'Auto Select."

---

