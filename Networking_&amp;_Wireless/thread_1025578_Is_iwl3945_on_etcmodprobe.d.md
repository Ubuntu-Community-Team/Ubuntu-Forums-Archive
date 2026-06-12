---
title: "Is iwl3945 on /etc/modprobe.d?"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by warpmaster on 2008-12-30
Hi

few days ago I installed Ubuntu in Acer Aspire 5600, with a Intel Pro Wireless 3945 ABG Pci Card. I found the solution to the issue of this pci card on this forum, here

[http://ubuntuforums.org/showthread.php?t=820297&page=2](http://ubuntuforums.org/showthread.php?t=820297&page=2)

But unfortuneatly, the problem appears again. When I reboot or shutdown, WIDIC not show any Wireless network. Then I check messages with dmesg and the error is the same

iwl3945: Radio disabled by HW RF Kill Switch

After do some test and solutions that **chili555** proposes I get the wireless switch on again. But is not stable. But my question is another. I think that Ubuntu loads iwl3945 by default on each boot, but I don't see iwl3945 in modprobe.d
```

**# ls -ls modprobe.d**
aliases
alsa-base
arch
arch-aliases
blacklist
blacklist-framebuffer
blacklist-modem
blacklist-oss
blacklist-watchdog
fuse
i2c
isapnp
libpisock9
libsane
lrm-video
options
toshiba_acpi.modprobe
```

I don't understand completey how works modprobe and rmmmod. But if Im not wrong, this commands add or remove modules of kernel in real-time.So this modules must be on /etc/modprobe.d or someplace. But I didn't find it :confused:

Is my first question to solve lately my issue with Intel 3945.

Thanks!

Ubuntu ussed: 8.10 Desktop Edition 2.6.27.9-generic

---

### Post by warpmaster on 2008-12-31
Nobody can help me? :S

---

