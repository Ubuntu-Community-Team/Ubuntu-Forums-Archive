---
title: "Ati radeon x700 pro. Driver help"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by celeron D on 2007-06-19
I downloaded the latest x700 pro. driver from ati's web site (now owned by AMD, so it's ati.amd.com) and when I opened the installer file, it automatically opened in "gedit" and "gedit" couldn't open it. I right-clicked on the file, and "opened with another application" and chose terminal, but that did not work either. Then, I downloaded the check.sh file from ati's website, to see if I had the right requirements, but this is what I got, ```
root@user-desktop:/home/user/Deskt op# bash ./check.sh
================================== ================================== =
 ATI Technologies
================================== ================================== =
You are either not running this sc ript from the console
or simply do not have console owne rship.  Requirement failed.
Unable to determine XFree86 Versio n. Stopping now.

```

Do you know how I can run the installer file, and also run the check file?

Thanks very much :D

Edit: here's the exact URL for the drivers and the test application: [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by celeron D on 2007-06-20
Does anyone know??

---

### Post by perlwonk on 2008-05-03
Did you make sure the file is executable? run chmod + x on the file and try again.

---

