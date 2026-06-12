---
title: "Wireless disconnects"
date: 2013-04-09
forum: Networking &amp; Wireless
---

### Post by mario.almeida on 2013-04-09
Hi All,

```
OS Ubuntu 12.10 64bit
TOSHIBA TECRA R950
Linux remy-nb 3.5.0-27-generic #46-Ubuntu SMP Mon Mar 25 19:58:17 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

I have wireless issue, wireless connection disconnect by its self and will prompt to enter for wireless password, even if I re-enter it do not work, I tried even to disable and enable wireless but not luck. Only option is to reboot my laptop.

Any suggestions?

//Remy

---

### Post by mario.almeida on 2013-04-20
Following in the syslog file

> Apr 20 16:00:50 remy-nb kernel: [19805.544682] ath: phy0: DMA failed to stop in 10 ms AR_CR=0xffffffff AR_DIAG_SW=0xffffffff DMADBG_7=0xffffffff
Apr 20 16:00:50 remy-nb kernel: [19805.544702] ath: phy0: Could not stop RX, we could be confusing the DMA engine when we start RX up
Apr 20 16:00:50 remy-nb kernel: [19805.625700] ath: phy0: Failed to stop TX DMA, queues=0x10f!
Apr 20 16:00:50 remy-nb kernel: [19805.765524] ath: phy0: Chip reset failed
Apr 20 16:00:50 remy-nb kernel: [19805.765535] ath: phy0: Unable to reset channel, reset status -22
Apr 20 16:00:50 remy-nb kernel: [19805.765558] ath: phy0: Unable to set channel

---

