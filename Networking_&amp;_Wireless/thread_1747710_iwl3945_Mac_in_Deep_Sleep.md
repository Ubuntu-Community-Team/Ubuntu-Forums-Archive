---
title: "iwl3945 Mac in Deep Sleep"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by jameswang07 on 2011-05-02
So, it's another "Mac in Deep Sleep" problem.  Running iwl3945, my laptop is a Sony Vaio VGN-NR160E, running the Intel GM965 card.  I haven't run the other cmds yet, but I have a dmesg up.  I'll add more stuff on request.  I've had this problem consistently over 3 different Ubuntu distros for the past 3 years: Xubuntu, Ubuntu, Mint (and have been too lazy to post, basically the only way to fix this problem is a restart of the system).

---

### Post by dannyboy79 on 2012-10-27
I am having the same problem

```
[   35.007203] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   35.007206] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   35.007295] PCI: Enabling device 0000:0b:00.0 (0000 -> 0002)
[   35.007305] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   35.007325] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[   35.007344] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   36.578640] iwl3945: MAC is in deep sleep!
[   36.578668] iwl3945: Unable to int nic
```

Does anyone have any solutions? It doesn't happen all the time. Sometimes I'll shut the lid of my Sony VAIO laptop and when I open the lid the wireless card is fine but something I'll open it and I get the error you see in the dmesg output above.

---

