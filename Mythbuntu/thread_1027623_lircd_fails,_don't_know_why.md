---
title: "lircd fails, don't know why"
date: 2009-01-01
forum: Mythbuntu
---

### Post by bartvh on 2009-01-01
A few hours ago I plugged out my remote control receiver and plugged it into another USB port.
Now, LIRC won't start anymore. I'm not sure if it's related, but I guess it must be.

entering /etc/init.d/lirc start or service lirc start just gives me "starting lirc [fail]".
This is so frustrating! What use is this to me? I want to know why.

By googling I found out that lirc should log to syslog. However, /var/syslog contains nothing about LIRC.

I can manually start lircd. This apparently works, and it says so in the syslog. However, it's no real use because the correct info isn't given to it.

What can I do to find this problem?

---

