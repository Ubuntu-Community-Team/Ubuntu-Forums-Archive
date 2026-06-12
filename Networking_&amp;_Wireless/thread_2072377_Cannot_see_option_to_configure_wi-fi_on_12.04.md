---
title: "Cannot see option to configure wi-fi on 12.04"
date: 2012-10-17
forum: Networking &amp; Wireless
---

### Post by anthonysaulnier on 2012-10-17
Im on a desktop computer on a dual boot configuration (XP and Ubuntu 12.04) and purchased a USB Dlink DWA 121 wireless adapter.  It was working on Ubuntu, but stopped working all together.  As a matter of fact I dont even see the option now enable/disable wireless networks or connect to wireless networks in the top right corner.  I tried switching usb ports but that did nothing.

I know the adapter works fine on Windows on the same machine.  Kinda lost at this point.  I know some people see the option to enable wireless but its greyed out, but in my case I dont see anything period.  And wlan0 is not detected either.

I will say that when it was working unbuntu, the connection was kinda flaky.


Any ideas?

---

### Post by anthonysaulnier on 2012-10-17
I found out that the chipset on the adapter is a realtek chipset, rtl8192c, so I downloaded the linux version of the driver and installed it using ./install.sh . When i install it it seems to detect my wireless adapter and will unsuccessfully attempt to connect to my router.

However, when I reboot the computer, everything is back at square 1, nothing detected.  I go through the install process again, same thing, reboot again and same thing nothing is detected until i go to install the driver again.

Any help will be very much appreciated.

---

### Post by ahallubuntu on 2012-10-17
You need to add the newly built driver/module to the end of the file /etc/modules so it will automatically be loaded at each boot.  Also, if you update Ubuntu to a newer kernel, you'll have re-build the module again.

---

### Post by anthonysaulnier on 2012-10-18
Thanks for the info.

Sounds like this could be an bit of a nuisance.  I will give it a try.

---

