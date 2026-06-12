---
title: "Mythbuntu (11.04, 10.10, 10.04) MSI P67A-GD55"
date: 2011-08-28
forum: Mythbuntu
---

### Post by Lester_Burnham on 2011-08-28
Hi,

I'm having issues with a new setup.
Motherboard: MSI P67A-GD55
CPU: i3 2100T
HDD: Samsung F4 2tb
Tuners tried: Hauppauge Nova-T 500 x 2 (with LNA options enabled), hvr-2200
```
options dvb-usb-dib0700 force_lna_activation=1
options dvb_usb disable_rc_polling=1
```

It seems to work at first, if you're watching TV, but then later it seems as if the signal has decreased!! Recordings are all pixelated and unwatchable.

The channels scan OK, but after a period of idling, tuners seem to have no signal.

I'll add some lspci, dmesg and grep dvb later.

Thanks,
Lester

ps. dmesg was too large to attach, so I'll attach it another way later.

---

