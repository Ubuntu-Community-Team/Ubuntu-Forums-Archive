---
title: "Ekiga user permissions"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by kix on 2007-01-05
Hello

Trying to get Ekiga working for the first time and encountered a couple of problems,  any one with knowledge please help.

Running Ubuntu 6.10, up to date , web cam is working in the default user, but under a second user with desktop privileges, the web cam will not initialise.

cd /usr/bin
sudo ./ekiga--config-tool --fix-permissions

Tried again to run from the second user, no web cam.  Default user can still see web cam output.

If web cam iinitialises  from default user, and activiation led is on, still won't initialise with the other user.

Anybody know what is needed to get this running under other users?  Permission change somewhere?

thanks

Kix

---

### Post by GatorDog on 2007-08-22
in Ekiga-   Edit > Preferences > Video Devices

Try setting the "channel" to the same number as in the account that works.

If that doesn't get it, I also tried this somewhere along the way-
In an effort to "use a bigger hammer" I set the permissions on the video device.
ie  chmod 777 /dev/video0.

rod
Feisty 7.04

---

