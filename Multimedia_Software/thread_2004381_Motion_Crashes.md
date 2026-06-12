---
title: "Motion Crashes"
date: 2012-06-15
forum: Multimedia Software
---

### Post by gary441 on 2012-06-15
Motion crashes when I set it up to monitor a IP camera.
I'm running XUbuntu 12.04 on a Panasonic Toughbook CF-28. Was working great on XUbuntu 10.10, but had to upgrade. Only thing that is different I can think of is I'm using lighttpd instead of apache. This is a fresh install, not a upgrade from 10.10.
When it does crash, it does make a "_usr_bin_motion.115.crash" file, but I don't see much in there to help me.

In motion.conf, I have to use "netcam_url ftp://IP" instead of http: cauase it isn't working with http:

Any ideas?

Thanks,
Gary

---

### Post by gary441 on 2012-06-15
I think it's fixed. I had to keep trying.
I changed the target_dir to /tmp/motion in the config and it has not crashed in 20 minutes. Hasn't taked and pics, but hopefully that works, too.
Atleast it has not crashed.

Gary

---

