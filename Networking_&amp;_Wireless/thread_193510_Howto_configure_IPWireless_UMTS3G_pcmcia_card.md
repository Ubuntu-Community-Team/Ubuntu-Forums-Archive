---
title: "Howto configure IPWireless UMTS/3G pcmcia card"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by krunkite on 2006-06-10
Help! I'm tearing my hair out!

I'm a relative noob to Linux, let alone Ubuntu, but I reckon I'm getting the hang of the installation process on my system. I was running Breezy till yesterday and have now migrated to Dapper.

However, as with the previous version I'm still stumped as to how to successfully compile the drivers for my IPWireless umts/3g pcmcia card! Looks just like this: 

[http://www.ipwireless.com/solutions/pcmcia.html]("http://www.ipwireless.com/solutions/pcmcia.html")

Is this type of modem recognised by Ubuntu as a USB or serial device?

I've found a number of threads on the configuration issue:

[http://www.pharscape.org/index.php?option=content&task=view&id=28]("http://www.pharscape.org/index.php?option=content&task=view&id=28")
(This is probably the best thread for me, being that it's so simple......and for a different type of manufacturer, but I'll change some of the details.)

[http://www.wlug.org.nz/WooshWireless]("http://www.wlug.org.nz/WooshWireless")

[http://www.ubuntuforums.org/showthread.php?t=66194&highlight=ipwireless]("http://www.ubuntuforums.org/showthread.php?t=66194&highlight=ipwireless")

[]("http://www.neology.co.za/support/index.php?page=MyWirelessLinuxDrivers")

In the last thread, Rodent suggests:
 "Edit the **Kconfig** file in /usr/src/linux-2.6.0/drivers/usb/serial/Kconfig," and "/usr/src/linux-2.6.0/drivers/usb/serial/Makefile."

Do these files actually exist in the path above on Ubuntu? I've run a search and can't find them. Can't help thinking that I'm looking for something with a slightly different name in a different path!](*,) 

Or do I just need to edit this file with the necessary card info: /etc/modprobe.conf.local 

and forget about 'Kconfig'?

I'm probably very, very stupid!:-? 

Thank you for any help in advance.

---

