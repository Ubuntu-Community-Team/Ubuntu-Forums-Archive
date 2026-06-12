---
title: "EMU 1616m sound card not working"
date: 2010-10-04
forum: Multimedia Software
---

### Post by zoboraman on 2010-10-04
Hello All,

I have a EMU 1616m sound card and I can not get it to work with Ubuntu 10.04 or 10.10. At the boot sequence I get the message that firmware could not be loaded. However, when I use another Linux distro PARDUS that uses KDE, the card works perfectly. With KUBUNTU i don't get any chance either. I think it is a kernel problem but both distros have the same kernels. 

So, this is not a KDE vs GNOME problem either as KUBUNTU did not work it either.

Can anyone help me about this? Please?

---

### Post by zoboraman on 2010-10-04
gokhan@gokbuntu:~$ dmesg | grep emu
[    9.221112] emu1010: Special config.
[    9.221236] emu1010: EMU_HANA_ID = 0x3f
[    9.221277] emu1010: filename emu/emu1010b.fw testing
[    9.653161] firmware: emu/emu1010b.fw not found. Err = -2
[    9.653211] emu1010: Loading Firmware file emu/emu1010b.fw failed

---

### Post by zoboraman on 2010-10-04
gokhan@gokbuntu:~$ dmesg | grep 1010
[    9.221112] emu1010: Special config.
[    9.221236] emu1010: EMU_HANA_ID = 0x3f
[    9.221277] emu1010: filename emu/emu1010b.fw testing
[    9.653161] firmware: emu/emu1010b.fw not found. Err = -2
[    9.653211] emu1010: Loading Firmware file emu/emu1010b.fw failed
gokhan@gokbuntu:~$ dmesg | grep EMU
[    9.221034] EMU10K1_Audigy 0000:04:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.221236] emu1010: EMU_HANA_ID = 0x3f
[    9.653824] EMU10K1_Audigy 0000:04:01.0: PCI INT A disabled
[    9.653878] EMU10K1_Audigy: probe of 0000:04:01.0 failed with error -2

---

