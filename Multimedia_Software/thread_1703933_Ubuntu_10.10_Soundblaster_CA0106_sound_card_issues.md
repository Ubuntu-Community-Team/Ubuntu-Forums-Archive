---
title: "Ubuntu 10.10 Soundblaster CA0106 sound card issues"
date: 2011-03-09
forum: Multimedia Software
---

### Post by t1mulid on 2011-03-09
How I can duplicate issue. Power up, select Ubuntu from grub menu, boot Ubuntu 10.10 and all sounds play as high volume static. When I left click the speaker ICON and select sound preferences then hardware then test speakers then Front Left Test static is played on right speaker. Right Front Test plays static on left speaker. If after a power on I boot Windows 7 through grub then restart and boot Ubuntu 10.10 through grub sound works OK. Can someone explain how to fix this issue?

Output from sudo lshw -c sound

```
*-multimedia
             description: Multimedia audio controller
             product: CA0106 Soundblaster
             vendor: Creative Labs
             physical id: 7
             bus info: pci@0000:01:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=CA0106 latency=32 maxlatency=20 mingnt=2
             resources: irq:17 ioport:df00(size=32)
```

---

