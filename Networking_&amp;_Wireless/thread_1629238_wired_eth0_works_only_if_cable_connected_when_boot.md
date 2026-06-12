---
title: "wired eth0 works only if cable connected when booting"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by jtjk on 2010-11-23
Hi,

I am running Ubuntu 10.04 in Hp Mini 5103 netbook.

Network connection works well if cable is physically connected immidiately when machine is powered on.

However if connected without cable and connecting cable after boot, there seems not be way to get connection working without boot.

ifconfig does not show eth0 and if trying to call that, it says device not found.

Initially wired connection did not work at all, but I added followed lines to grub.conf and then I got it working like described above.

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_os_name=Linux"

Any help?

---

