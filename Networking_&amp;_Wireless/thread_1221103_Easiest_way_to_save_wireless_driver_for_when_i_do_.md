---
title: "Easiest way to save wireless driver for when i do a fresh install"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by colllin on 2009-07-23
I am currently running jaunty, but I would like to do a fresh install. Is there a way I can save the broadcom b43 wireless driver to a cd or usb. I want to avoid having to drag my desktop to the router (which is what I ended up doing last time).

---

### Post by spd106 on 2009-07-23
Yep, the driver has shipped with Ubuntu since around 8.04, all you need are the (non-redistributable) firmware files in the /lib/firmware/b43 folder. Just copy them over to your new install and reload the b43 driver (or reboot).

The firmware is usually good for using in across different kernel versions as there's no strict ABI dependency, but you might need to update the firmware if you have upgraded to a new release (i.e. new kernel), there will be a message in the syslog if this is the case. You can get the latest version from linuxwireless.org, just remember that in this case you'll need to use the b43-fwcutter tool.

---

