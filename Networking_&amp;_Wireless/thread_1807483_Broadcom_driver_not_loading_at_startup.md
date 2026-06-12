---
title: "Broadcom driver not loading at startup"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by weirdwolfvortex on 2011-07-19
Hi all,

I have been struggling with the Broadcom driver for my friend's Lenovo Thinkpad E420. What I have done is installed kernel 3.0.0 rc7 and 2.6.39.3, both successful, but unable to start up either. So, I was thrown back at 2.6.32-33. Well, due to no out-of-box support for the driver, I manually compiled and installed the broadcom driver.

Now, I am able to use the wireless on the laptop but the problem is that it does not load automatically on startup. Everytime I boot up, I have to run this command:

```
cd hybrid_wl/ && sudo modprobe lib80211 && sudo insmod wl.ko
```Now, I need help with the driver to start it at login.
```

$ lspci
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
00:1c.7 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 8 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1c49 (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
03:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 04)
08:00.0 Network controller: Broadcom Corporation Device 0576 (rev 01)
```Another small problem is that even when connected, the network applet shows the disconnected icon. But when clicked on it, it shows the connection and other available networks.

Any help with these will be greatly appreciated. :)

---

### Post by westie457 on 2011-07-19
It definitely looks like an issue with drivers. 
Maybe this link will help with the problem.

[http://ubuntuforums.org/showpost.php?p=10801185&postcount=240](http://ubuntuforums.org/showpost.php?p=10801185&postcount=240)

As far as I am aware this will fix 90% - 100% of all Broadcom diver issues.

Good luck.

---

