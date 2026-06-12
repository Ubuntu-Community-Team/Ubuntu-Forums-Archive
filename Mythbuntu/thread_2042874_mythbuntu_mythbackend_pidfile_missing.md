---
title: "mythbuntu mythbackend pidfile missing"
date: 2012-08-15
forum: Mythbuntu
---

### Post by ederopaa on 2012-08-15
I'm trying to set up monit to monitor and restart my mythbackend, which occasionally tends to freeze. I think it is possibly related to some DVB-T tda10046 driver issues...But I cannot find a mythbackend pidfile for the normal monit setup:

```
check process mythbackend with pidfile /var/run/mythtv/mythbackend.pid
 group mythtv
 start program = "/etc/init.d/mythtv-backend restart"
 stop program  = "/etc/init.d/mythtv-backend stop"
 if failed port 6544 proto http then restart
 mode manual
 depends on mysql

check process mysql with pidfile /var/run/mysqld/mysqld.pid
 group mythtv
 start program = "/etc/init.d/mysql start"
 stop program = "/etc/init.d/mysql stop"
 if failed port 3306 then restart
 mode manual
```

/var/run/mythtv/ is empty.

Any ideas on how to get things up and working?

---

### Post by ederopaa on 2012-08-16
Ok, so now I know why there isn't a pidfile:

> since ubuntu moved to using upstart it no long writes a PID file for mythbackend. Do you need monit with upstart for mysql and mythbackend? If so, for mythbackend you'll want to do something like modify the /etc/init/mythtv-backend.conf upstart configuration to write a PID file and give the PID file proper permissions.

How do I configure /etc/init/mythtv-backend.conf to write a pidfile?

---

### Post by nickrout on 2012-08-16
At a guess, add a line to the script along the lines```
pidof mythbackend > /var/run/mythtv/mythbackend.pid
```

---

