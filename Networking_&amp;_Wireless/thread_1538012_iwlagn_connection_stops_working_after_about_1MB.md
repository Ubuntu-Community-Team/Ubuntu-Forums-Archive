---
title: "iwlagn connection stops working after about 1MB"
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by smaring on 2010-07-24
I have an Intel PRO/Wireless 5100 AGN [Shiloh] on my HP Pavilion dv7 running a fully updated Lucid (10.04).

I can connect to the wifi on my smartphone and I have no problems at all.  However, after a recent update I found myself unable to use my home wifi connection.  Once connected, I can usually transfer about 1 MB of data and then nothing else will go through.

# uname -a
Linux lappy 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

Since the home wifi router, a Linksys Wireless-G SRX, is a bit more advanced than the wifi capabilities of the smartphone, I'm inclined to think there is some feature being used that is now broken in the iwlagn driver.

I've tried to disable the "11n" support with this:

# modprobe -r iwlagn
# modprobe iwlagn 11n_disable=1

but the problem continues even after that ... is there something else I can try to disable?  or some way of getting the details of these two connections to see exactly what the difference is?

Thanks,
Steve Maring

---

### Post by smaring on 2010-07-26
I uninstalled NetworkManager, installed WICD, and now I can connect and use my home network just fine.

---

### Post by boblettoj99 on 2011-10-12
Posted this in completely the wrong place...ignore me

---

