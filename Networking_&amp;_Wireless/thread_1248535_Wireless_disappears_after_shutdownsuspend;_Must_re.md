---
title: "Wireless disappears after shutdown/suspend; Must re-enable in BIOS!"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by tarsius4 on 2009-08-24
Hello,

I'm using Ubuntu 9.04 via a wubi install on my Asus EeePC 1000HA. I've had this netbook for over 9 months with the same Ubuntu installation without any problems, but I've noticed the following issue for the past week (probably due to an update):

When everything is normal, my wifi works fine.  However, once I suspend my computer, the wlan1 interface refuses to connect to my home network and "sudo iwlist scan" finds no networks.  After rebooting, the wlan1 interface has disappeared completely.  This persists over subsequent reboots.  After booting into Windows XP, the wireless interface is absent, but pressing "Fn-F2" (wireless toggle), the interface appears and works fine. If I now reboot to Ubuntu, the wifi will work once again.  I've since discovered that I can re-enable the wifi from the BIOS setup screen and thus the problem seems to be that Ubuntu disables the hardware during suspend and shutdown, but cannot re-enable it.

Note that disabling wifi has always presented a problem on my EeePC such that I've always had to reboot to re-enable it.  This is the first time I've been forced to enable it from the BIOS setup.  I should also mention that I've been using Statux's EeePC Tray ([http://www.statux.org/wiki/index.php?title=EeePC](http://www.statux.org/wiki/index.php?title=EeePC))

Since I believe Ubuntu is voluntarily shutting down the wifi before suspend and shutdown, I kept an eye on the blue wifi indicator light and noticed it turns off a moment before the power light turns off (or switches to suspend mode blinking).

Has anyone been experiencing this problem?
Steve

---

### Post by tarsius4 on 2009-08-24
SOLVED!  I started looking through information about the EeePC Tray and ACPI utilities and I found directions to allow Ubuntu to enable the wifi.
[http://www.statux.org/wiki/index.php?title=EeePC_ACPI_Known_Issues#WIFI_Toggle](http://www.statux.org/wiki/index.php?title=EeePC_ACPI_Known_Issues#WIFI_Toggle)

It seems that Ubuntu automatically re-enables the wifi, but the re-enable action was not functioning properly on my EeePC.

(by the way, this topic should not be labeled xubuntu... I am using ordinary Ubuntu 9.04 installed through wubi)

---

