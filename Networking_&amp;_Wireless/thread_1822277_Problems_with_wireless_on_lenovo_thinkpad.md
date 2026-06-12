---
title: "Problems with wireless on lenovo thinkpad"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by Ferroin on 2011-08-10
I'm trying to run Xubuntu 11.04 on a Lenovo Thinkpad E220s, but for some reason that I can't figure out, the kernel refuses to acknowledge that the wireless chip even exists.  I have checked and made sure that the kernel is loading the proper module with the driver for the Intel Centrino Wireless N-1000 chipset, updated the microcode, made sure Wi-Fi was enabled in the BIOS, and just about everything else that I can think of.  I know the chip it self works because Windows 7 and OpenBSD both work fine with it.

---

### Post by chili555 on 2011-08-10
How about the wireless switch? Does it work as expected? Please open a terminal and run and post:```
rfkill list all
```Thanks.

---

### Post by Ferroin on 2011-08-10
There's no external wireless switch, it's all just controlled by the BIOS, but the kernel did find the bluetooth chip and that is working correctly

---

### Post by Ferroin on 2011-08-10
Checked the output from dmesg, the kernel doesn't even seem to see the hardware at boot, which is odd because lshw does show it correctly

---

### Post by chili555 on 2011-08-10
> **Ferroin said:**
> There's no external wireless switch, it's all just controlled by the BIOS, but the kernel did find the bluetooth chip and that is working correctlyPlease run and post:```
rfkill list all
```Please see attached. Does your E220s not have that switch?

---

### Post by Ferroin on 2011-08-10
Tried the one thing that I hadn't yet. Installed the backported compat-wireless modules and now it works fine.[]("http://ubuntuforums.org/showpost.php?p=6183681&postcount=1")

---

