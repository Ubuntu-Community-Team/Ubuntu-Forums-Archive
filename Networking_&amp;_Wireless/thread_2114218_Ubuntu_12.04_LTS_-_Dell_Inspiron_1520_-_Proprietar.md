---
title: "Ubuntu 12.04 LTS - Dell Inspiron 1520 - Proprietary Driver for Broadcom"
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by xSCCMx on 2013-02-09
I would like to know if the Broadcom Linux STA Wireless driver offered by Ubuntu would make my wifi work. I didn't install it yet because I was worried that it may of grabbed the wrong thing, if anyone has successfully installed this driver, I would like to know if your Wi-fi worked properly.

---

### Post by praseodym on 2013-02-09
Which hardware is in use?

Please show:

```
lspci -nnk | grep -iA2 net
```

---

### Post by xSCCMx on 2013-02-09
Provided is the dialog box that gave me a notification of a driver that I can use along with the terminal command that you gave me in the screenshot. I wanted to be sure this was the correct driver before installing Ubuntu on my system.

---

### Post by praseodym on 2013-02-09
Ok, you dont need the proprietary driver. Just install the package "linux-firmware-nonfree" via cable. It contains the firmware for the native b43 driver.

Reboot.

---

