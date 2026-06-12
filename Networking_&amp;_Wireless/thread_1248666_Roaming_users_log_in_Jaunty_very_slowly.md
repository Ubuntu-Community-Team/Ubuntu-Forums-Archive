---
title: "Roaming users log in Jaunty very slowly"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by teknoman on 2009-08-24
Hi all.

I've recently installed Kubuntu Jaunty at our client PCs in our school. We had Gutsy before.
I have also installed KDE 4.3 through ppa backport repository.
Server still has Gutsy.

All users have their home directory mounted through NFS4. They also have corporate directories mounted in this way. They don't use the same PC always (that's the reason I said "roaming users" in the title).

All seems to work properly as before did, except one thing:

The first time an user logs in the system, it takes a long time (it's normal as it has to build all configuration files, KDE structure, etc...).
The second time takes much less time to log-in, from any PC.
It has been always so. 

But now it's different: 
The log-in process takes a long time every time the user uses a different PC. It only runs normally when the user log in a PC he had logged before.

Once he user is logged, all appear to run properly, except akonadi server (any idea to disable/remove it?, my users are not interested at all on it).

Could akonadi server be the reason of all it?

As we are in a school, nobody has a PC for himself. Everybody uses a PC that is available at that moment, so it's normal that a user logs in multiple PCs along the time.

Thanks in advance

---

