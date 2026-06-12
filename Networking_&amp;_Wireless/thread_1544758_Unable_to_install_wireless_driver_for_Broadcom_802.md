---
title: "Unable to install wireless driver for Broadcom 802.11b/g WLAN"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by Gowd H on 2010-08-02
I have Ubuntu 10.04 installed and can browse the internet via cable, but wireless isnt working. My wireless driver is  "Broadcom 802.11b/g WLAN".

In the windows device manager, I found the corresponding inf file to be oem20.inf which I tried to install it through "Setup Windows Driver" but it gave an error saying invalid driver. I also tried installing the Broadcom STA driver, but that didnot help.

I am dual booting with Windows 7, and i installed ubuntu through the windows wubi installer. My laptop is HP Pavilion dv4. I have installed the regular Ubuntu desktop and have made all upgrades. The results from lspci command i have added below.

Was it the wrong inf file? If so, where can i find the correct one. 

Am I doing it correct? Please HELP.

Thanks.


[LIST=1]
[*]gowda@ubuntu:~$ lspci
[*]00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
[*]00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
[*]00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
[*]00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
[*]00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
[*]00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
[*]00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
[*]00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
[*]00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
[*]00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
[*]00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
[*]00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
[*]00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
[*]00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
[*]00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
[*]00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
[*]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
[*]00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
[*]00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
[*]00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
[*]02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
[*]03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
[*]04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
[*]04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
[*]04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
[*]04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
[/LIST]

---

### Post by belkinsa on 2010-08-02
Sorry guys, he's my friend on a site and I have found the solution after an hour just chatting with him after the issue.  Turns out that there is a Linux driver to it.

---

### Post by jaywebguy on 2010-12-08
Are you talking about the 3rd party ones found under System/admin/hardware? I tried both. It seems my problem is that wifi wont turn on. I've got a red/orange light an when I run iwconfig it says its off. I try turning it on but it wont stick. Any idea?

> **Mechafish said:**
> Sorry guys, he's my friend on a site and I have found the solution after an hour just chatting with him after the issue.  Turns out that there is a Linux driver to it.

---

