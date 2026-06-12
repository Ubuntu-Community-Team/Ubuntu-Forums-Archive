---
title: "How to prevent mythbackend from starting up at boot"
date: 2010-01-20
forum: Mythbuntu
---

### Post by Eldis on 2010-01-20
I have a problem that my mythbackend starts up at startup despite my efforts of not having it start. I'm currently debugging a problem with one of my tuners and mythbackend is foiling my debugging of it. 

I've done update-rc.d -f mythtv-backend remove

And checkd my custom scripts that they don't start it. What else could be starting it ? I'm not starting the frontend either now on startup while debugging.

So something is waking up the backend any idea what could be doing it ?

This is the pf -ef

```
mythtv    1157  1062  0 19:33 ?        00:00:00 sh -c /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log
mythtv    1158  1157  1 19:33 ?        00:00:08 /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log
```

---

### Post by ian dobson on 2010-01-20
Hi,

If your running 9.10 then I imagine that upstart is starting your mythbackend. Have a look in your /etc/init directory at the file mythtv-backend.conf.

Maybe if you just rename the .conf file to something else, that could be enough to stop upstart from starting the backend.

Regards
Ian Dobson

---

### Post by Eldis on 2010-01-20
> **ian dobson said:**
> Hi,

If your running 9.10 then I imagine that upstart is starting your mythbackend. Have a look in your /etc/init directory at the file mythtv-backend.conf.

Maybe if you just rename the .conf file to something else, that could be enough to stop upstart from starting the backend.

Regards
Ian Dobson

Thanks a lot I think that will do it. I guess next time I know to google upstart.

---

