---
title: "Latest updates lost sound - Intel Corporation 82801G"
date: 2008-05-17
forum: Multimedia Software
---

### Post by kevindontenville on 2008-05-17
Hi

Anyone had this on the latest 2.6.17 header updates?  Reverted to previous and sound returns ok but the new updates definitely lost my sound.

lspci gives:
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

Before I post a bug does anyone have any ideas?

thanks!

K

---

### Post by nacnud on 2008-05-19
I have the same sound card, and the same problem....

---

### Post by kevindontenville on 2008-05-19
I did try installing virtualbox sometime ago and I wonder if that screwed the headers up somewhere. However the difference seems to be whether 386 or generic is loaded.

in /boot/grub/menu.lst the offending boot option was:

Ubuntu 8.04, kernel 2.6.24-17-386

When I select at boot (by pressing esc in the boot sequence and selecting it) the previous install :

Ubuntu 8.04, kernel 2.6.24-17-generic

all the sound comes back. 

When I check what sound modules are loaded with the offending boot option it returns none. Looked in the module headers but all the sane things look installed.

In the end I just switched the previous boot option as default so I don't need to intervene, but its not ideal!

At least I dont feel alone now! ;-)

K

---

### Post by Seine on 2008-05-20
I have the same issue with the same card. Thanks for posting, I now have a workaround.

Edit: [This (now fixed) bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200338") in launchpad may be the same issue.

---

### Post by kevindontenville on 2008-05-20
Glad to have helped a little. The bug is similar but not quite the same for me, so as there seem to be at least 3 of us I have posted a new bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/232154](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/232154)

Please feel free to add comment as you think ;-)

---

