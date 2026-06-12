---
title: "Why do I need to restart backend for it to work?"
date: 2009-03-19
forum: Mythbuntu
---

### Post by Afkpuz on 2009-03-19
Ok, I've installed ubuntu 8.10+mythtv on 3 different systems. On every one, I have to sudo killall mythbackend in order for it to work properly.  If I use the session manager to tell mythbackend to run on startup, it doesn't help.  The frontend doesn't receive any info from the backend.  So, does anyone else get this problem?  Why do I need to restart mythbackend on every single login?

---

### Post by nickrout on 2009-03-19
If the backend is not properly starting on bootup then the log should tell you why.

```
less /var/log/mythtv/mythbackend.log
```

The session manager should not have anything to do with it. mythbackend s started by an init script, ```
/etc/init.d/mythtv-backend 
```

It should be set to start in every runlevel. 

However I saw a problem recently where the backend was set to start before mysql, which obviously will not work. Check what order your scripts are set to start in.

```
ls /etc/rc2.d
``` (I think thats the directory)

---

### Post by mathog on 2009-03-20
> **nickrout said:**
> 
However I saw a problem recently where the backend was set to start before mysql, which obviously will not work. Check what order your scripts are set to start in.

```
ls /etc/rc2.d
``` (I think thats the directory)

Change the start order by renaming the links so that they look like this, then reboot, it should come up ok:

```

/etc/rc0.d/K20mythtv-backend -> ../init.d/mythtv-backend
/etc/rc1.d/K20mythtv-backend -> ../init.d/mythtv-backend
/etc/rc2.d/S99mythtv-backend -> ../init.d/mythtv-backend
/etc/rc3.d/S99mythtv-backend -> ../init.d/mythtv-backend
/etc/rc4.d/S99mythtv-backend -> ../init.d/mythtv-backend
/etc/rc5.d/S99mythtv-backend -> ../init.d/mythtv-backend
/etc/rc6.d/K20mythtv-backend -> ../init.d/mythtv-backend

```

If memory serves I had to do this because the network was coming up too slowly and that was screwing everything else up. The change above will work so long as all the other dependencies are not broken (network, mysql, etc.)

---

### Post by AboveTheLogic on 2009-03-24
mathog, thank you for that post

i had this same issue and following your steps seems to have resolved it... my tuner wasn't being recognized after startup and now it is

---

