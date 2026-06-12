---
title: "Tv Tuner Permissions"
date: 2008-10-19
forum: Multimedia Software
---

### Post by jake3988 on 2008-10-19
Hello, I'm trying to install a tv tuner on kernel 2.6.27 (the newest).

When I try and install dvb-utils and it attempts to create the dvb directories it claims udev (udevd) is running and then attempts to create the directory in /dev/.static/dvb/ which then fails because that's read-only.

I killed udevd and it still says it's running.

Is there any way I can secure the permissions to make this work?

Thanks!!

---

