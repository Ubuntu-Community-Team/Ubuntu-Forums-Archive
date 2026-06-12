---
title: "Time/Date errors"
date: 2006-04-10
forum: Networking &amp; Wireless
---

### Post by MightyTuna on 2006-04-10
I'm running breezy badger in an Active Directory Domain and I need the machine to run "net time set" at boot up and hourly in cron to keep the tyme syncronized to the domain's time. Unfortunately my scripts don't seem to be working.

I don't care if the machine syncs with an Internet server initially, but I need the last thing it does at bootup to be "net time set"

I have two scripts, both of which are set to allow world read and world execute:
/etc/init.d/local looks like this
#!/bin/sh

net time set

and /etc/cron.hourly/nettime.sh looks like this
#!/bin/sh

net time set


what am I doing wrong?

---

### Post by bscbrit on 2006-04-10
I haven't used net time set before, but from reading the man pages, it is used to set the time of 'this' computer to the time of the server.  Therefore, I think that you need something like

net time set -S nameofserver

However, I stress that I am reading the man page ('man net' on a command line / in a terminal) for the first time. :-|

---

