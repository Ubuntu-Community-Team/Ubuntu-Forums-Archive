---
title: "Can't enable subwoofer"
date: 2011-02-05
forum: Multimedia Software
---

### Post by soundgarden_ on 2011-02-05
My Laptop is MSI EX620 [http://www.msi.com/product/nb/EX620.html#/?div=Specification](http://www.msi.com/product/nb/EX620.html#/?div=Specification)
On clean install (ubuntu 10.4 32bit...and so on older versions) I have no sound. After edit /etc/modprobe.d/alsa-base.conf and put this line
options snd-hda-intel model=targa-2ch-dig
...sounds word on both left and right speakers . But my laptop si 2.1 audio system and i can't run sounds on subwoofer. Please, give me a solution

---

### Post by soundgarden_ on 2011-02-05
lspci -v | grep Audio -A 8
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Micro-Star International Co., Ltd. Device 6740
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at fdef8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
--
06:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
    Subsystem: Micro-Star International Co., Ltd. Device aa28
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at febec000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

---

