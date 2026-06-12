---
title: "Cannot get Echo GIna 3G to work properly."
date: 2007-08-22
forum: Multimedia &amp; Video
---

### Post by leaphion on 2007-08-22
I have just installed a brand new xubuntu on my desktop, but it doesn't seem to work with ALSA at all. I can see the Motorola chipset in lspci, possible modules in lsmod, and I already installed the alsa-driver package from source up, but it seems that it doesn't work yet.

Edit: Okay, I checked the dmesg, and there it said that 

ALSA /usr/src/alsa/alsa-driver-1.0.14/pci/echoaudio/echoaudio.c:47: get_firmware(): Firmware not available (-2)
Echoaudio Echo3G: probe of 0000:01:00.0 failed with error -2

So, I installed the alsa-firmware package from source up.
Now it says:

Echoaudio Echo3G: probe of 0000:01:00.0 failed with error -5

Above that are these two lines:

ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 17 (level, low) -> IRQ 17
ACPI: PCI interrupt for device 0000:01:00.0 disabled

Something to do with those?

---

### Post by leaphion on 2007-08-23
Sorry to bump this a bit, but isn't there anyone who could help me with this problem?

---

### Post by amias on 2007-11-06
I'm getting the same problems with a layla3g on on ubuntustudio.

The firmware doesn't seem to be included in the alsa packages.

---

