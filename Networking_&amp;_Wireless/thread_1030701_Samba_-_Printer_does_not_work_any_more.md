---
title: "Samba - Printer does not work any more"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by Lancerlan on 2009-01-04
Hello
I am running Hardy Heron on a desktop computer and I have Printer (Epson CX3810) connected to that computer. I installed SAMBA, but I haven't bring able to print in that Epson Printer using the wireless connection of laptop which has windows XP. Also after installing SAMBA, the printer does not print anything at all. (not even form the desktop).

I got the following log info from the CUPS, but I dont know what to do next. I will appreciate any ppossible help.

 /var/log/cups/error_log
I [04/Jan/2009:16:58:09 -0500] [Job 195] Started backend /usr/lib/cups/backend/usb (PID 10688)
I [04/Jan/2009:16:59:49 -0500] [Job 195] Canceled by "daniel".
I [04/Jan/2009:16:59:52 -0500] [Job 193] Started filter /usr/lib/cups/filter/pstops (PID 10780)
I [04/Jan/2009:16:59:52 -0500] [Job 193] Started filter /usr/lib/cups/filter/foomatic-rip (PID 10781)
I [04/Jan/2009:16:59:52 -0500] [Job 193] Started backend /usr/lib/cups/backend/hal (PID 10782)
I [04/Jan/2009:16:59:52 -0500] [Job 194] Canceled by "daniel".
E [04/Jan/2009:16:59:52 -0500] PID 10782 (/usr/lib/cups/backend/hal) stopped with status 1!
I [04/Jan/2009:16:59:52 -0500] Hint: Try setting the LogLevel to "debug" to find out more.
E [04/Jan/2009:16:59:52 -0500] [Job 193] Unable to open device "hal:///org/freedesktop/Hal/devices/usb_device_4b8_818_L39020601240136180_if1_printer_noserial": Permission denied


Thanks
Lancerlan

---

