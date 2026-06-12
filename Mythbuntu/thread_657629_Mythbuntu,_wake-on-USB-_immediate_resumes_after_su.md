---
title: "Mythbuntu, wake-on-USB- immediate resumes after suspend to ram"
date: 2008-01-03
forum: Mythbuntu
---

### Post by purdueee on 2008-01-03
I'm trying to get STR (S3) and wake from USB using a USB-UIRT. STR is working without issue, system enters and resumes nicely as long as /etc/acpi/wakeup shows the USB ports as disabled for wakeup. If I enable some of the ports, I get an immediate resume. I found some traffic on the kernel mailing lists about ehci_hcd and ohci_hcd causing immediate resumes so I modprobe -r both before suspend. This allows the computer to stay suspended but then the USB wake doesn't work (not that it did before). I also get usb over-current warnings on occupied ports on resume, but everything is working ok (checked for dust,shorts,etc)

Here's what I've checked:
BIOS: All USB options enabled, STR(S3) enabled, Wake-on-USB enabled
MoBo: Jumpers installed to provide standby power to USB ports, checked ok w/ DMM, USB-UIRT blinks while system is suspended in response to IR traffic.
USB-UIRT configured on my windows PC to enable wake-on-usb using lrnhelper_0_0_5 (also tried version 3)

SW:
Mythbuntu 7.10 (64bit)
2.6.22.14-generic (default kernel)

Here's my hw:
Biostar TF7050-m2 MoBo
USB-UIRT
Antec Fusion case with VFD
Leadtek WinFast 2000XP Deluxe analog tuner
hdhomerun digital tuner

---

