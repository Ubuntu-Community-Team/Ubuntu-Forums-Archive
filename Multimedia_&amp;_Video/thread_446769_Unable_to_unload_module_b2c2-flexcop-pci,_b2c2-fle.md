---
title: "Unable to unload module b2c2-flexcop-pci, b2c2-flexcop to allow wake up from acpi"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by bing on 2007-05-17
Hello,

I've encountered the most annoying situation with feisty. ACPI S3 standby (suspend to ram) works fine on my machine, except that after I resume (by pushing the power button), my Technisat AirStar HD5000 tuner card doesn't tune anymore. A reboot restores the situation. I'm running mythtv-0.20-fixes svn 13444.

My (very limited) debugging suggests that acpi is having trouble unloading the kernel module for the tuner card and that's the problem. When I try to manually remove the module with rmmod or modprobe -r (as root) for the relevant modules, b2c2_flexcop_pci and b2c2_flexcop, I get the following error:

FATAL: Module b2c2_flexcop_pci is in use.

I've already checked out the dependencies - no problem there.

My theory is that being unable unload the tuner module is the root of the wake up problem with acpi. Any suggestions for unloading modules?

Thanks,
Bing

EDIT:
For anybody else experiencing wake up problems with acpi standby with any peripherals while running mythtv, I figured out what the problem is.
1. First configure mythtv-setup, under Capture cards, Recording options, to "Open DVB card on demand" - otherwise the dvb driver is locked while mythbackend is running
2. As root, edit /etc/default/acpi-support and look for the following line starting with MODULES
    MODULES="[your dvb drive module name here]", e.g., MODULES="b2c2-flexcop-pci"
    This will unload the driver during acpi s3 standby and then reload it upon resume.

This will allow you to enable acpi power saving and also allow you to schedule recordings with mythbackend, giving you a warm fuzzy green feeling while also being a couch potato.
Check these links out for more information.
[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)
[http://www.mythtv.org/wiki/index.php/ACPI_Wakeup](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup)

---

