---
title: "stop mediatomb auto starting at boot"
date: 2012-06-30
forum: Multimedia Software
---

### Post by tyn on 2012-06-30
Hi,
I am running Ubuntu 12.04 server with Mediatomb installed from apt-get.  It works fine except I don't want to it always auto start at boot time.  I changed the /etc/default/mediatomb file so that NO_START="yes" but it just keeps on auto starting.

Does anyone know what else needs to be modified to make Mediatomb stop auto-starting at boot time?


The reason I want to stop the auto-starting is because there my ZFS file system isn't mounted before Mediatomb starts.  This causes the configuration in Mediatomb to be lost every time I reboot.  If I ever get some time I'll put in a patch to Mediatomb to fix this...

My solution is to stop the auto-starting and make sure my ZFS file systems are mounted in rc.local, then start mediatomb up.  Simple enough.


You help is greatly appreciated.
Ty

---

### Post by Grubbie on 2012-09-09
Greetings,

Have you tried to remove it from your init by running the following?

sudo update-rc.d -f mediatomb remove 

The -f is to force the removal if mediatomb is present and running, and it sounds like yours is.

If that doesn't work, you should try:     sudo /etc/init.d/mediatomb stop     Or:   sudo service mediatomb stop

It depends on which kernel you're running.....you won't hurt anything using either one.

I hope this is helpful.

kevin

---

