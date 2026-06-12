---
title: "Can't get DWL-520 rev. E to work."
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by XtinaS on 2009-05-24
I'm using Ubuntu 8.04, 32-bit version.  I have a DWL-520 rev. E.

I've gone over these documents:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)
[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

I installed the driver via D-Link's own site - got the WinXP driver, and installed it using... something that installed System > Administration > Windows Wireless Drivers.  (I've been doing this all day, so I can't recall what did what.)  It finds the hardware.  It seems fine.  But iwconfig doesn't show anything for wlan0, and iwlist wlan0 scan returns "Interface doesn't support scanning".

What do I do?

---

### Post by Praveer on 2009-05-24
I couldn't get it working with ndiswrapper either. I used hostAP and it worked untill the latest release... Tell me if you have any luck!

EDIT: You might want to check this out: [http://ubuntuforums.org/showthread.php?t=643467&highlight=dwl+520+rev](http://ubuntuforums.org/showthread.php?t=643467&highlight=dwl+520+rev)

---

### Post by vbic on 2009-11-09
Same for me. I have been using the advices on [http://ubuntuforums.org/archive/index.php/t-643467.html](http://ubuntuforums.org/archive/index.php/t-643467.html) successfully until I upgraded to Ubuntu 9.10, where my system did not even start up.

After various fiddling, I figured out it comes from prism2_srec which now stalls the whole system when trying to load firmware on the DWL 520 E1 card, with such command as
$ /usr/sbin/prism2_srec -gs wlan0 /lib/firmware/Latest-prism/primary-RAM/pm010102.hex

If someone has an idea of what changed between 8.10 and 9.10, I would really be gratefull...

---

