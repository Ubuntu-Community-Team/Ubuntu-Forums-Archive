---
title: "Where is lirc started"
date: 2012-04-30
forum: Mythbuntu
---

### Post by Saubazi on 2012-04-30
I am having some problems with lirc, after the update to 12.04.
When I have booted up lirc is running but not working. I stop lirc, remove
ir_lirc_codec lirc_serial and lirc_dev modules, restart lirc and it works.
Now I removed lirc service with update-rc.d but still when I boot, lirc is running - so what gives? What is starting lirc?

Moreover - I don't know what ir_lirc_codec is doing but after I restart lirc and let it load the modules it does not load that module. I also tried to put that into /etc/modprobe.d/blacklist-lirc.conf file but still the module is there after the boot.

---

