---
title: "NVIDIA Driver causes hang"
date: 2010-05-09
forum: Multimedia Software
---

### Post by infecticide on 2010-05-09
I have just upgraded my Ubuntu Server to 10.04 and have had two hiccups.

1. The first boot-up after the upgrade it decided to run a filesystem check without any indication of what it was doing.  I eventually figured out what the hell it was doing.

2. I run BOINC with the idle time (there is lots) and have installed an NVIDIA GeForce 9800GTX to enable CUDA computation.   When I compile the module and the install program loads the module, I see the kernel messages but the machine locks up with no crash information.   The module worked fine before the upgrade and I have blacklisted the nouveau module.

```

[ 1237.288818] nvidia: module license 'NVIDIA' taints kernel.
[ 1237.299304] Disabling lock debugging due to kernel taint
[ 1237.875425] ACPI: PCI Interrupt Link [LMC9] enabled at IRQ 22
[ 1237.886234] nvidia 0000:00:0d.0: PCI INT A -> Link[LMC9] -> GSI 22 (level, low) -> IRQ 22

```

Once the module loads the server becomes completely unresponsive.

```

vgaarb: device changed decodes: PCI:0000:00:0d.0,olddecodes=io+mem,decodes=none:owns=io+mem
vgaarb: transferring owner from PCI:0000:00:0d.0 to PCI:0000:02:00.0

```

I don't recall seeing this "vgaarb" reference before, could this be part of the issue?

---

### Post by infecticide on 2010-05-09
Interesting... I changed the order of graphics adapters in the BIOS from IGP to PCIE and moved the connector from the onboard to the PCIE card and now the module loads fine.

---

