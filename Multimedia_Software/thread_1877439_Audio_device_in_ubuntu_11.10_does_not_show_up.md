---
title: "Audio device in ubuntu 11.10 does not show up"
date: 2011-11-08
forum: Multimedia Software
---

### Post by kiyu2keith on 2011-11-08
My device seems like it does not show up in the sound settings and since I'm new in ubuntu I really don't know how to fix it. I tried several things from forums but to no avail.

aplay -l:
aplay: device_list:240: no soundcards found...

lspci -v:

80:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)
    Subsystem: Micro-Star International Co., Ltd. Device 7253
    Flags: fast devsel, IRQ 17
    Memory at <ignored> (64-bit, non-prefetchable)
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel


this is the output I get when I type those commands.

Can you give me any solution that may work??

Thanks in advance..

---

### Post by lisati on 2011-11-08
Closed by request of OP: duplicate of [http://ubuntuforums.org/showthread.php?t=1877452](http://ubuntuforums.org/showthread.php?t=1877452)

---

