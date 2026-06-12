---
title: "Wake on USB"
date: 2011-04-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by teachop on 2011-04-09
My Natty beta1 laptop wakes from suspend correctly (nice).  However, usb keyboard will not wake it up, only if it is open and I hit the laptop keyboard.  I have tried echoing everything but the kitchen sink at /proc/acpi/wakeup and /sys/bus/usb/devices/xxxx/power/wakeup with no change.  Any ideas?
```
Bus 002 Device 006: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 005: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 138a:0005 DigitalPersona, Inc 
Bus 002 Device 003: ID 050d:0307 Belkin Components 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device	S-state	  Status   Sysfs node
P0P2	  S4	*disabled  
PEGP	  S4	*disabled  
P0P3	  S4	*disabled  
PEGP	  S4	*disabled  
P0P1	  S4	*disabled  pci:0000:00:1e.0
PS2K	  S3	*enabled   pnp:00:07
PS2M	  S3	*disabled  pnp:00:08
EHC1	  S3	*disabled  pci:0000:00:1d.0
USB1	  S3	*disabled  
USB2	  S3	*disabled  
USB3	  S3	*disabled  
USB4	  S3	*disabled  
EHC2	  S3	*disabled  pci:0000:00:1a.0
USB5	  S3	*disabled  
USB6	  S3	*disabled  
USB7	  S3	*disabled  
HDEF	  S0	*disabled  pci:0000:00:1b.0
RP01	  S4	*disabled  pci:0000:00:1c.0
RP02	  S4	*disabled  pci:0000:00:1c.1
PXSX	  S5	*enabled   pci:0000:03:00.0
RP03	  S4	*disabled  

```

---

### Post by lucazade on 2011-04-09
If I remember correctly there is a way to force unloading of usb modules before suspend, this way they should wake correctly.

Have you also tried to suspend using commandline? You can try differents "quirks" to see if you find a working one for you laptop.
```
man pm-suspend
```

Have you seen in /var/log/pm-suspend.log or dmesg for errors?

---

### Post by teachop on 2011-04-09
Thanks for the help.  Wasn't able to progress in that direction but it was educational (wonder if that would have helped me get suspend working on some systems in the past!).

I should be able to flip the "disabled" to "enabled".  I can do it for PS2M for example, but not USB1.  Also tried enabling the hub in /sys/bus/devices/xxx/power/wakeup along with it, and that doesn't do anything either. A cat /sys/bus/devices/xxx/power/wakeup says enabled, but the cat /proc/acpi/wakeup is stubbornly stuck on disable for the USBx.

---

### Post by lucazade on 2011-04-09
what about adding this kernel option?

acpi_sleep=s3_bios
[http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/re72.html](http://www.linuxtopia.org/online_books/linux_kernel/kernel_configuration/re72.html)

---

