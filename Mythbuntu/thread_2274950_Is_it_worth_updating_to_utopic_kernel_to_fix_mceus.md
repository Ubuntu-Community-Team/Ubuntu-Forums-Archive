---
title: "Is it worth updating to utopic kernel to fix mceusb &amp; usb3 problem"
date: 2015-04-23
forum: Mythbuntu
---

### Post by frackers2 on 2015-04-23
Greetings all

When I installed Mythbuntu some 6-7 months ago I couldn't use the usb3 ports with my mce remote until I hacked in a 3.14 kernel.

Since the LTS Enablement updates have released a 3.16 kernel, is it worth updating to it and its associated X stack?

Cheers

---

### Post by ian-weisser on 2015-04-24
One easy way to find out is to create a 14.10 or 15.04 LiveUSB.
If the hardware is detected, then the kernel upgrade is worthwhile.

---

### Post by uteck on 2015-04-30
You can update the kernel from the backports repo to use the newer kernel and not risk the rest of your setup.  If it does not work, reboot and select the older working kernel and remove the new one.  I think the backports repo is included in most installs, but disabled.

---

