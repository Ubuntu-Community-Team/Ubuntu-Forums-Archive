---
title: "dmesg output for ipw2200 on 10.04"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by sarloth on 2010-07-28
Good afternoon,

I was wondering if anyone using Intel Pro Wireless 2200bg would mind posting the output of the following command:

```
dmesg | grep ipw
```

I don't currently have access to my laptop but I am trying to do some searches on the firmware versions before I get home and start working on it.

Nevermind, found it after some harder searching:

```

[   23.372888] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   23.372895] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   23.613446] ipw2200 0000:02:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   23.624106] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   23.624193] ipw2200 0000:02:02.0: firmware: requesting ipw2200-bss.fw
[   23.965666] ipw2200: Radio Frequency Kill Switch is On:
[   24.233276] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)

```

---

### Post by chili555 on 2010-07-28
> ipw2200: Radio Frequency Kill Switch is On:That's undoubtedly the only thing keeping your wireless from working. Post back if you can't click over the hardware switch and get it going.

---

### Post by tgalati4 on 2010-07-28
Works fine using Jaunty on a thinkpad T43p:

tgalati4@tpad-Gloria7 ~ $ dmesg | grep ipw
[   14.388715] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   14.388719] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   14.388793] ipw2200 0000:0b:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.389527] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   14.389575] ipw2200 0000:0b:02.0: firmware: requesting ipw2200-bss.fw
[   14.645327] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)

---

