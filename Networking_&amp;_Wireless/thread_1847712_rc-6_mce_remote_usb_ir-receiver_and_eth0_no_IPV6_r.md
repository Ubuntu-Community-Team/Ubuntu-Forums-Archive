---
title: "rc-6 mce remote usb ir-receiver and eth0: no IPV6 routers present boot hang..."
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by pils92 on 2011-09-21
Well I didn't know if this was a network problem or hardware, but here goes. I have a rosewill RC-6 MCE infrared remote, this remote works fine. The IR receiver is usb and attached to a 6' cord, every other boot the computer will hang at "eth0: no IPV6 routers present" for around 3 minutes and then boot to the desktop with the mouse and keyboard completely unresponsive. After a restart all boots fine and things are again normal, until the next restart.... If the IR receiver is unplugged the machine works without fail. Though I have also seen this using a Virgin mobile 3G usb dongle made by novatel.

My box is a 3.2ghz p4, 3ghz ddr2 667mhz, biostar 945gc-m4 motherboard, and nvidia gt240 graphics.

Logitech MX5500 usb bluetooth mouse and keyboard.

Ubuntu 10.10 kernel version 2.6.35.30-generic.

---

### Post by pils92 on 2011-12-18
May have solved, the problem seems to be with the mceusb driver being included in the kernel after 10.10. After adding "blacklist mceusb" to /etc/modprobe.d/blacklist.conf then running "update-initramfs -u -k all" and a reboot all was back to normal functionality. I can only assume this was because the still more functional mceusb modules installed in earlier releases were getting in the way of the new kernel modules.;)
A side Note on the kernel modules, I would not recommend using them if you were already using the old modules as the button presses are not programmed the same. This is a nuisance if like me you have programmed buttons into ir-exec

---

