---
title: "Help with Airport-Utils"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by jacrider on 2010-10-28
I started a search to see if there is an application to manage Apple's Airport/Time Capsule routers.  

There appears to be a package airport-utils that is supposed to be able to allow a Linux box to administer one of these devices.

I have installed it and can't seem to get it to start.  Can anyone give me an idea of how to use this application?  I have searched all over the web and haven't found much.  There is no documentation on the launchpad site:  [https://launchpad.net/ubuntu/+source/airport-utils](https://launchpad.net/ubuntu/+source/airport-utils)

Anyway, if anyone can shed any light on this, I would appreciate it.  My other option is to remote desktop into one of my kids Macs to do my admin.

Thanks.

---

### Post by jackdale on 2010-12-02
Bump


(I've also been looking at how to actually use these utils with lucid and maverick with no luck so far).

---

### Post by daniel_w93 on 2010-12-14
Well to start them up you have to open a terminal and put in any of these commands

For AirPort
```
airport-config
```

For AirPort Extreme
```
airport2-config
```

However when I do this it returns a Java error...would be interesting to hear what others got.

I googled around a little and found out, that apparently it works with the Sun Java5 jre/jdk. So could it be that because Ubuntu 10.10 uses Open Java6 it gives me the error?

---

### Post by beringse on 2010-12-18
I've looked around as well for a way to view my timecapsule config. Since the connection is solid guess I'll hang loose until something is developed.

---

