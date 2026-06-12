---
title: "Can no longer remotely connect to MySQL"
date: 2008-04-15
forum: Mythbuntu
---

### Post by uncle hammy on 2008-04-15
I have been working at setting up an XBox frontend for my setup (not so much fun actually).

Anyways, up until now, I have been using MySql Administrator and Query Browser from a windows machine to do things such as back up my MythTv database.

Today I find that I am no longer able to connect to the db with either of these tools, using either the root user or the mythtv user.  I can ping the server fine, I can connect to MySql from my backend/frontend box fine (obvisouly, if I can run some of the commands below), and everything is still working (mytv, mythweb).  I have no frontends right now, but I am even able to use MytvPlayer from my windows machine fine.

The only changes I have made to my setup since it last worked yesterday were to run...

dpkg-reconfigure mythtv-databse (and set a root password)
dpkg-reconfigure mythtv-common (and actually made no changes)

and I ran this to supposedly give access on my subnet...

grant all on mythconverg.* to mythtv@"172.16.1.%" identified by "mythtv"; 
flush privileges;

Anybody have any ideas on what I can do to get this back?  It was a very convenient way for me to run backups.

---

### Post by tgm4883 on 2008-04-16
Not sure about your issue, but just FYI, the latest build of XBMC has mythtv support built in

---

### Post by uncle hammy on 2008-04-16
I know, that's why I ended up running the dkpg-reconfgures and the grant all commands.

When I add myth://mythtv:mythtv@192.168.1.116 (obviously corrected for my setup) as a video source in xbmc, it can't connect.

---

### Post by uncle hammy on 2008-04-16
OK, it was my "identified by" part of the grant all.  I was putting the user in again, instead of the password.  Working again.  Though I still haven't been able to get xbmc to connect.

---

