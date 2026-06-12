---
title: "Updates broke my wireless.."
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by fatsamurai on 2009-04-28
I installed a load of updates yesterday (security updates, I think) and since then the Network Manager applet refuses to display wifi connections. It doesn't even mention wireless at all, almost as if the adaptor is not there.

Things I have checked:

ath_pci module is loaded (kernel module for the wifi adaptor). Also tried swapping this module for another compatible one. Both modules load fine. No errors.

Output from message log:

```
Apr 28 09:05:09 aspireone kernel: [   10.823309] ath_hal: module license 'Proprietary' taints kernel.
Apr 28 09:05:09 aspireone kernel: [   10.827737] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Apr 28 09:05:09 aspireone kernel: [   10.869657] wlan: 0.9.4

```

```
Apr 28 09:05:09 aspireone kernel: [   10.995139] ath_pci: 0.9.4
Apr 28 09:05:09 aspireone kernel: [   10.995355] ath_pci 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr 28 09:05:09 aspireone kernel: [   11.044112] ath_pci 0000:03:00.0: PCI INT A disabled
```

It's really annoying. Suggestions?

I'm using 9.04.

---

### Post by coffeeaddict22 on 2009-04-28
what's the output of ```
iwconfig
``` and ```
lshw -C network
```; also ```
nm-tool
```

---

