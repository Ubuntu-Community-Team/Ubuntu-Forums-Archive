---
title: "satellite A505 with ubuntu 10.04 no wireless on dlink router"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by toobsco42 on 2010-04-30
I have a toshiba satellite A505 and i installed ubuntu 10.04 on my machine.  i have a dlink router and am able to connect to the internet in ubuntu 9.10 on my old toshiba.  however i have been poking around blogs and have seen that there are some issues with the realtek driver on the new toshiba's.  i have downloaded the driver and tried to compile but when i do make it has errors.  i also blacklisted rt2800usb module. additionally i edited the file /etc/default/grub (Grub 2.0) and modified option for GRUB_CMDLINE_LINUX_DEFAULT="acpi=off" and saved it. i opened up the terminal and typed: sudo update-grub. Rebooted the system.  the network applet picks up other routers. but does not pick up mine. i am out of ideas, has anyone else ecountered a similar situation with wireless not working in ubuntu 10.04?

---

### Post by menour on 2010-04-30
i have the laptop 

i only get blank screen before install and after:confused::confused::confused: boot from live disk with acpi=off" only


don't know have our ubunto team ignore some thing like this, reported as bug and solved

now i am looking for other option or help

---

