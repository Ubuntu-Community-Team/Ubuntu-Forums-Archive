---
title: "Restarting lirc"
date: 2012-05-30
forum: Mythbuntu
---

### Post by someitalian123 on 2012-05-30
My remote won't work unless I use the following 2 commands

sudo /etc/init.d/lirc stop
sudo /etc/init.d/lirc start

After I use these it works fine, but I have to redo this every reboot. Is there anyway to have this be done automatically at boot, or a way to actually fix the problem?

---

### Post by nickrout on 2012-05-30
try putting those two lines in /etc/rc.local

or simply ```
service lirc restart
```

---

### Post by someitalian123 on 2012-05-30
It works thank you

---

