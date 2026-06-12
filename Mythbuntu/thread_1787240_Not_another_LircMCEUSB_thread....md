---
title: "Not another Lirc/MCEUSB thread..."
date: 2011-06-20
forum: Mythbuntu
---

### Post by gwar11d2 on 2011-06-20
Here is the issue:
Can't get USB MCE remote to work.
Two identical systems (except for Nvidia Graphics in one, but that shouldn't matter).
One works perfect with lirc, the other does not (arrow keys work but that is about it...I think my livingroom myth box might think it is a usb keyboard)

Have tried to remove/reinstal/configure lirc on the non-working system to no avail.  Even copied /etc/lirc files from the working and ~/.lirc ...  nothing

Only thing I see different is that /dev/lirc0 is missing on the non-working which I think is the issue, but I can't seem to get that device to register no matter what I have tried.  I've been pounding on the keyboard for about 3 days now and I'm not sure what else I can check.

Any suggestions on where else to look?

Here is what happens when I plug the remote via dmesg:

[  304.704032] usb 5-1: new full speed USB device using uhci_hcd and address 3
[  304.907453] Registered IR keymap rc-rc6-mce
[  304.907674] input: Media Center Ed. eHome Infrared Remote Transceiver (1784:0011) as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/rc/rc1/input5
[  304.907806] rc1: Media Center Ed. eHome Infrared Remote Transceiver (1784:0011) as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/rc/rc1
[  304.907909] mceusb 5-1:1.0: Registered Topseed Technology Corp. eHome Infrared Transceiver on usb5:3

^^which is why I think it's not working the right way...

---

