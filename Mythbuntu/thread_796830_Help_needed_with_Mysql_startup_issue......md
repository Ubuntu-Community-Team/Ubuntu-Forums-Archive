---
title: "Help needed with Mysql startup issue....."
date: 2008-05-16
forum: Mythbuntu
---

### Post by lumpmonkey on 2008-05-16
Hi everyone,

Having a weird problem with mysql at the moment, it won't start up on boot! Running the init.d script manually works fine no errors, but when rebooting mythtbackend is not connecting to the database and the status of mysql is "stopped"

I've been playing with the startup order a bit to make sure it has time to startup before mythbackend, currently as follows:

S18mysql-ndb-mgm
S20mysql-ndb
S22mysql
S27mythtv-backend (I ommited any others inbetween to save space!)

I can't seem to find any logs that would give me any error output of the mysql startup script, scratching my head now! 

Many thanks

Andy

---

### Post by ian dobson on 2008-05-17
Hi,

I had afew problems with the startup of mythbackend, in the end I changed S27mythtv-backend  to S99mythtv-backend which solved the problem for me.

Regards
Ian Dobson

---

### Post by lumpmonkey on 2008-05-18
Hi, just tried that but it had no effect........mysql just seems to refuse to start on system boot! :(

Any other ideas?

---

