---
title: "Samsung monitor fails wakeup from standby"
date: 2009-01-16
forum: Multimedia Software
---

### Post by IQRules on 2009-01-16
This is 8.10 64-bit server, press power button, system wakes up. I can remote login ssh to it.

But monitor does not wake up. It worked 1 week ago, I did play with acpitool and modified /etc/init.d/halt script. Also I did couple times of apt-get update/upgrade.

I might want to refresh this with 8.04 64-bit.

If anyone can provide some helps, I could do quick troubleshooting.
Thanks

---

### Post by IQRules on 2009-01-17
This is quite amazing on this issue.
It has PM (Power management /etc/pm), acpi (/proc/acpi/wakeup) and /etc/init.d/halt all could be related to this.

Well, do we have best practice guide or simple trouble shooting guide? The video driver is Nvidia, not open source driver.

Can be this msg mean something?

[ 2829.886425] gnome-screensav[8077] general protection ip:7f9c68c92168 sp:7fff777defe0 error:0 in libc-2.8.90.so[7f9c68bfa000+169000]

---

