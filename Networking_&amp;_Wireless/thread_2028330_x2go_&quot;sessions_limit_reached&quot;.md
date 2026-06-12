---
title: "x2go &quot;sessions limit reached&quot;"
date: 2012-07-18
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2012-07-18
Hello,

I've been using x2go client for some time to connect to a x2go server (remote access).

Recently, I've attempted to connect using x2go client and receive an error message for the first time, that says "sessions limit reached".

Anyone know how to reset this?

---

### Post by DapperMe17 on 2012-07-18
When I use NoMachines NX client to connect to the server through SSH, connection works fine. So, there should be no issues with SSH or XSession limits on the server, relative to X2Go. 

Any other ideas?

---

### Post by citinetbot on 2012-07-19
in x2goserver.conf you have two sections about limits
just add your username and some value or value for a group

[limit user]
admin=2

or

[limit group]
x2gousers=10

---

### Post by DapperMe17 on 2012-07-20
Thanks CitiNetBot.

I decided to remove & purge the all related x2goserver files and reinstall, which of course, solved whatever conflict existed.

---

