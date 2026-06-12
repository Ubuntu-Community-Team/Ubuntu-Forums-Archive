---
title: "wpa supplicant problem - Driver Busy"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by lat2005 on 2008-12-23
My MBP 4,1 has triple boot:
Mac OS X
Windows XP
Ubuntu Intrepid 8.10

I enabled the wireless driver (Broadcom), but I haven't been able to use wpa_supplicant despite configuring it correctly.
I need it because nm-applet (GNOME Network Manager) doesn't work for all the networks I need to connect to.

The error I get is:
ioctl[SIOCSIWMODE]: Device or resource busy

Does anyone know how do I get control and enable wpa_supplicant to work? I tried killing nm0-applet and Network Manager but it doesn't help.

Should I use the BCM driver from the Mac OS X cd? I used this in the past and it worked, but using the driver already given seems better.

Thank you

---

