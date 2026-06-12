---
title: "ATI driver/fglrx difficulties"
date: 2008-01-15
forum: Multimedia &amp; Video
---

### Post by Buzzards on 2008-01-15
I loaded the ati driver/fglrx and now my screen is so messed up that I can not navigate.  Is there a way to change back to the default driver before the login screen appears?

Thanks

---

### Post by Melcar on 2008-01-15
<ctrl> <alt> F1

That takes you to command prompt mode.  Once there just reconfigure your xserver and start from scratch:

sudo dpkg-reconfigure xserver-xorg

... and chose vesa as your driver (everything else you can accept the default option, unless you now the exact values).

---

