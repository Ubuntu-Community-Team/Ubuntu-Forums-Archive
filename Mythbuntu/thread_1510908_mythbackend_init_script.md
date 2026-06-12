---
title: "mythbackend init script?"
date: 2010-06-16
forum: Mythbuntu
---

### Post by falcon15500 on 2010-06-16
Hi all,
  I am using mythbuntu 10.04 with the weekly builds turned on.  Today I did an update and the update appears to have removed my /etc/init.d/mythbackend init script.

  I have found a temporary replacement (generic) on the net, but would rather have the proper one back.  Can someone please paste in their init script?

M.

---

### Post by analogue on 2010-06-16
Ditto but I'm on karmic

cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

cat mythbuntu-repos.list 
deb [http://ppa.launchpad.net/mythbuntu/repos/ubuntu](http://ppa.launchpad.net/mythbuntu/repos/ubuntu) karmic main
deb [http://ppa.launchpad.net/mythbuntu/0.23/ubuntu](http://ppa.launchpad.net/mythbuntu/0.23/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/mythbuntu/0.23/ubuntu](http://ppa.launchpad.net/mythbuntu/0.23/ubuntu) karmic main


cd /etc/init.d
ls -l | grep -i myth
<nothing>

---

### Post by tgm4883 on 2010-06-16
We use upstart now. You should be able to do

```
service mythtv-backend start
```

or stop, status, etc

Is the backend having trouble starting?

---

### Post by falcon15500 on 2010-06-16
Using services, it complains that mythbackend is not a recognised service?

This literally happened before my eyes. Was working - running etc. Ran the updates, which naturally stopped the backend. And when updates were finished the backend was still not running. Went to start it how I usually did - from /etc/init.d but the script (which may have just been a wrapper for upstart) was gone. Tried services but no go. 

M.

---

### Post by tgm4883 on 2010-06-16
After further research, we should still be shipping that script for compatibility. I'll continue to look into that.

The service is actually called. 
```
service mythtv-backend start
```

---

### Post by falcon15500 on 2010-06-16
> **tgm4883 said:**
> After further research, we should still be shipping that script for compatibility. I'll continue to look into that.

The service is actually called. 
```
service mythtv-backend start
```

Tried that string as well and it IS recognised but upstart isn't starting it at boot. I noticed a lot of upstart jobs still have an entry in init.d so I added mythtv-backend and it works. Thanks for your help.  

M.

---

