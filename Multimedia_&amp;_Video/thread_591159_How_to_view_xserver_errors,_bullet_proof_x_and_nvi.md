---
title: "How to view xserver errors, bullet proof x and nvidia driver on custom kernel?"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by marzipan on 2007-10-25
Hi, i upgraded from 7.04 to 7.10.
Sorry for many questions put into this one post ;)

With 7.04 you had the option to view the xserver error log on failed xserver start. With 7.10 you have bullet proof x, which is nice, but doesnt show why the xserver didnt start. Is it possible to view the log?
I looked in /var/log but the Xorg logs didnt show errors.
Is bullet proof x maybe saving them somewhere else?
Is it possible to shutdown bullet proof x?

The reason i ask is this, i have nvidia 8600gts, and want to use a custom built kernel and also nvidia graphics driver. Because building restricted modules for a custom kernel is too hard for me ;) i want to install the regular linux drivers from nvidia.com. 
I did so before 7.10 when ubuntu didnt have restricted modules for my 8600GTS.

But when booting a custom kernel, and installing the nvidia driver, setting Xorg.conf, restarting gdm, the nvidia driver fails for a reason i cant see because of bullet proof x.

And because i cant kill bullet proof x, i have to go through its menu to setup nv driver, and then kill gdm again for another try with installing nvidia driver. (nvidia driver refuses to install when an X server is running)

---

### Post by khughitt on 2007-10-25
Heya,

Try **/var/log/Xorg.0.log** for the  log. Not sure about the other points though.

Take care,

---

