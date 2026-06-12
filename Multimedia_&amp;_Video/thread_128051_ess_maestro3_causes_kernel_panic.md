---
title: "ess_maestro3 causes kernel panic"
date: 2006-02-10
forum: Multimedia &amp; Video
---

### Post by tjfs on 2006-02-10
This driver on my hp laptop causes a kernel panic UNLESS you press Alt-F1 to turn off the graphical boot screen! If you remove 'splash' from the grub entry you get a full blown kernel panic when hotplug loads the driver. If you don't do anything special the system dies when it gets to hotplug in the boot sequence. Is there a later version of the driver I can try? Thanks.

lspci -v|grep audio returns:
0000:00:0d.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator

The last few lines of the kernel panic are as follows:

[4294745.431000] [<d014600a>] alsa_card_m3_init+0xa/0xc [snd_maestro3]
[4294745.431000] [<c01297c6>] sys_init_module+0xb5/0x172
[4294745.431000] [<c0102ef9>] syscall_call+0x7/0xb
[4294745.431000] Code: Bad EIP value.
[4294745.431000] <0>Kernel panic - not syncing: Fatal exception in interrupt
[4294745.431000]

If you get it to load (by pressing Alt-F1 at boot time) modinfo gives:

filename: /lib/modules/2.6.12-10-386/kernel/sound/pci/snd-maestro3.ko
description: ESS Maestro3 PCI
vermagic: 2.6.12-10-386 386 gcc-3.4
srcversion: ED7980D97712981A8573787

lsmod reports:

snd_maestro3 23332 1

---

