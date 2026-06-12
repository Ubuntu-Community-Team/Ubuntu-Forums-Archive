---
title: "After hibernate, lucid wireless stopped working"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by hoink on 2010-10-09
I recently installed 10.04 and everything Just Worked.

Before Lucid, I was using 9.04 and had successfully gotten my Broadcom 4306 working perfectly... which is why I think the Lucid install went so perfectly.

Well, after a botched hiberation (Dell Inspiron 9100), my wireless is dead in the water.

I've tried "ifdown", "iwconfig", "/etc/init.d/network restart" and "force-reload", 'modprobe -r b43'...


What can I do to get my wireless working again?!

---

### Post by P4man on 2010-10-10
THink its a problem with the killswitch. If the hardware switch isnt helping, try this:
```

sudo rfkill unblock all
rfkill list
```

---

