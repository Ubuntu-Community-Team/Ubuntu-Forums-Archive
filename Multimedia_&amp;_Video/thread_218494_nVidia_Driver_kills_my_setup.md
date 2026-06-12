---
title: "nVidia Driver kills my setup"
date: 2006-07-18
forum: Multimedia &amp; Video
---

### Post by serpicolugnut on 2006-07-18
I am running Dapper 6.06 on a custom built AMD3400 with a GeFore FX 5200 GPU. When I install the Nvidia driver and restart X, the monitor goes black and then about 30 seconds later, the monitor goes in to standby mode.

If I restart in recovery mode and restore the xorg.conf file from the backup, I can then restart X and GDM and everything is fine. 

Of note, I had this same problem during the Dapper Beta cycle. I had hoped it would be fixed by the release. 

Anybody have any idea on how I might fix this? The FX 5200 is listed as supported. Could it be something in the xorg.conf and my monitor? I have a ViewSonic VE170b 17" LCD.

Thanks!

---

### Post by meng on 2006-07-18
How did you install the nvidia drivers? By repository or binary?

---

### Post by tseliot on 2006-07-18
It's a known issue. The Nvidia staff knows more than me about it (try asking them for help):
[www.nvnews.net/vbulletin/forumdisplay.php?f=14](www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by serpicolugnut on 2006-07-18
I've tried both ways - repository and binary, and I get the same end result - dead X server.

---

### Post by serpicolugnut on 2006-07-18
OK, so it appears to be a conflict between the drivers and the kernel used in 6.06. The kernel that was in 5.10 worked fine with the drivers.

So the question is:

Is it possible to use the kernel from 5.10 in 6.6, and if so, will that still allow me to use the XGL/Compiz stuff...

And alternatively, I was thinking about upgrading the graphics card anyway... Is there is good card (ATI or nVidia) that will fully work w/ the drivers under 6.10 and will allow the use of XGL/Compiz?

Thanks - T

---

### Post by meng on 2006-07-18
Would "sudo dkpg-reconfigure xserver-xorg" be of any use in this situation? Seems a shame to go back to 5.10 and/or an earlier version of the nvidia drivers.

Thanks tseliot for mentioning the issue, else I would not have known. Myself, I've been lucky and haven't encountered these problems.

---

