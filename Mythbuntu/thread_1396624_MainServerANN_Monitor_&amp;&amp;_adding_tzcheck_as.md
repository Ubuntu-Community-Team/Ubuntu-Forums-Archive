---
title: "MainServer::ANN Monitor &amp;&amp; adding: tzcheck as a client (events: 0)"
date: 2010-02-02
forum: Mythbuntu
---

### Post by jayman8547 on 2010-02-02
mythbackend.log is just filled with 

2010-02-02 09:39:53.403 MainServer::ANN Monitor
2010-02-02 09:39:53.434 adding: tzcheck as a client (events: 0)

Not a lot of info out there but I've found a few other people that have had this issue.

I think it has to do with slave backends not being found.  I do not have an slave BE's but in order for mythfrontend.log to be created on my frontends I had to enable them as slave backends and then disable them.

Is it possible the backed is still looking for those backends?  If so would a database cleanup / optimization do the trick?

[http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance#Optimize_the_Database](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance#Optimize_the_Database)

---

### Post by jayman8547 on 2010-02-04
Nobody really had any answers but I stumbled upon a google hit that talked about slave backends.  I had to change one of my FE's to a slave BE in order for the logging to work.  In my haste, I never disabled the slave BE, hence the loads of error messages.

So if anyone finds this post and is having the same logging issues as described, you have a slave backend somewhere on your system.

---

### Post by tuskentower on 2011-10-14
Thanks for the tip. For anyone else landing up here, I have a BE (back end) and FE (front end) on separate machines.

I went to the FE and found a backend running:
```

zot@zot:~$ ps -ef | grep -i myth
zot      2304     1  2 Oct06 ?        04:58:36 /usr/bin/mythfrontend.real --logfile /var/log/mythtv/mythfrontend.log
mythtv    5124     1 60 00:33 ?        00:00:00 /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log --user mythtv
1000      5127  5081  0 00:33 pts/0    00:00:00 grep --color=auto -i myth

```

I shut down the BE service with this command:
```

zot@zot:~$ sudo service mythtv-backend status
mythtv-backend start/running, process 5215
zot@zot:~$ sudo service mythtv-backend stop
mythtv-backend stop/waiting

```

I permanently disabled the BE service with this command:
```

zot@zot:~$ sudo update-rc.d -f mythtv-backend remove
 Removing any system startup links for /etc/init.d/mythtv-backend ...

```

---

