---
title: "Built-in ethernet not registering"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by _H3MLOCK on 2010-06-14
Ok, so I have ubuntu 10.04 running on an old computer. The motherboard is an L7VMM2 Rev 1.1
Initially everything was running smoothly, then I brought it upstairs and everything just failed. The computer would hang right before the POST memory check, and after a few reboots it would do the memory check and reboot. So, I opened it up and switched the RAM around thinking it may have been a BIOS bug or a loos connection and it seemed to work. Now it boots into 10.04 perfectly and is blazing fast for an old computer. THe only problem now is that according to ubuntu, my ethernet controller is non-existent. It doesn't show up in lspci, dmesg and the only thing in ifconfig is the lo interface. It will however recognize the USB interfaces. I upgraded to linux 2.6.2.32-22-generic #33 but that didn't help the issue any. Now I'm stuck, and running out of ideas. Help would be greatly appreciated.

---

### Post by Iowan on 2010-06-14
From a terminal (Applications>Accessories>Terminal) **sudo lshw -C network** should provide more information about your interface.

---

### Post by _H3MLOCK on 2010-06-14
I had already tried lshw, and there's nothing there. The expression you specified returns no output. mii-tools says that no mii interfaces were found either

---

