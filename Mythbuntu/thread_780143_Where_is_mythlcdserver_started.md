---
title: "Where is mythlcdserver started?"
date: 2008-05-03
forum: Mythbuntu
---

### Post by Juzz on 2008-05-03
Hiyas,

I have an iMon VFD and have setup LCDd to startup as a service (by using update-rc.d).

However it seems that mythlcdserver is loaded up before LCDd - as it is only the heartbeat that is showing when mythfrontend is launched.

I can't seem to figure out where mythlcdserver is started up, if I could then I could perhaps do something to have mythlcdserver load up after LCDd.

Regards
Juzz

---

### Post by wombo on 2008-05-03
Mythtv requests for Mythlcdserver to startup.

There is an option to output to LCD in the config.

---

### Post by joshp on 2008-05-07
I have the same problem.  Its the same device and ever since the upgrade to hardy the LCD displays the SERVERS: X CLIENTS: X screen until I restart mythfrontend.  Did you find any solution?
Thanks,
-Josh

---

### Post by slyhne on 2008-05-13
Hi

I'm having this problem as well.

If I ssh into my MythTV computer and kill mythlcdserver mythfrontend will start mythlcdserver automatic and connect.

I noticed that I had to kill it 2 times before it connected

```
$ killall mythlcdserver
$ killall mythlcdserver
```

There must be some timing issue.

I could write a script that kills mythlcdserver after startup, but thats not a solution.

Does anyone know what the right solution is?

Regards

slyhne

---

### Post by Globemaster on 2008-06-09
Hi,
I had the same problem and I think I solved it. I used sysv-rc-conf (apt-get install sysv-rc-conf) to change the starting of LCDd. In the LCDd row I set "S" enabled. Now it works for me (again).

Hope this helps,
Globemaster

---

### Post by ironstorm on 2008-06-21
I have this problem, supposedly there is a bug in mythfrontend which doesn't init the connection to LCDproc properly...  

There is a whole thread on it, this was the last post about it:
[http://www.mythtv.org/pipermail/mythtv-users/2008-April/220795.html](http://www.mythtv.org/pipermail/mythtv-users/2008-April/220795.html)

---

### Post by sebrock on 2008-08-04
Was this solved by anyone? Is there a proper solution. I seem to have the exact same problem, killing mythlcdserver makes it work :confused:

Would be nice to know what this is...

---

### Post by ppww on 2009-03-09
Just confirming that this is still a problem today, in Mythbuntu 8.10.
Ubuntu bug report at [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/133640]("https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/133640") recommends promoting LCDd in the start sequence so it has plenty of time to initialize before mythlcdserver starts.

I have done this and verified that it works on my system:
```
# update-rc.d -f LCDd remove
 Removing any system startup links for /etc/init.d/LCDd ...
   /etc/rc0.d/K60LCDd
   /etc/rc1.d/K60LCDd
   /etc/rc2.d/S60LCDd
   /etc/rc3.d/S60LCDd
   /etc/rc4.d/S60LCDd
   /etc/rc5.d/S60LCDd
   /etc/rc6.d/K60LCDd

# update-rc.d LCDd defaults
 Adding system startup for /etc/init.d/LCDd ...
   /etc/rc0.d/K20LCDd -> ../init.d/LCDd
   /etc/rc1.d/K20LCDd -> ../init.d/LCDd
   /etc/rc6.d/K20LCDd -> ../init.d/LCDd
   /etc/rc2.d/S20LCDd -> ../init.d/LCDd
   /etc/rc3.d/S20LCDd -> ../init.d/LCDd
   /etc/rc4.d/S20LCDd -> ../init.d/LCDd
   /etc/rc5.d/S20LCDd -> ../init.d/LCDd

# reboot
```

"/usr/bin/mythlcdserver -v none" is hardcoded into the mythfrontend.real executable; that's why it's so difficult to figure out how/where it is started, and how to change its behavior, including logging.

As I noted in the link above, the best fix would be to have mythlcdserver retry its connection to LCDd periodically, if it finds LCDd unavailable at any time.

---

