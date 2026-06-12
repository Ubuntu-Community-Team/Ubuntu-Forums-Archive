---
title: "Mythfrontend won't start after upgrade"
date: 2010-08-15
forum: Mythbuntu
---

### Post by linuxhippy on 2010-08-15
I've been using mythbuntu on my home theatre system since 9.10 and then upgraded to 10.04 months ago.  This morning I did an update and then an upgrade before shutting down.  Now mythbuntu boots fine till it autostarts mythtv when I get a set up screen requesting my language and the next screen says NO UPnp then stops.

If I press ESC I can get to the Database Configuration screens which are already filled in with password, username and connection port.  It won't except these when I press finish.

Ideas?

---

### Post by linuxhippy on 2010-08-16
Well I shut it down and went without TV for a day and tried it again later and now it boots fine.

:)

---

### Post by Caysho on 2010-08-18
There is a bug in ubuntu 10.04, not all services are started during boot. (bug 543506 or 554172).

I have the same issue, and it is the mysql service that is not running.
> 
sudo /etc/init.d/mysql start


and maybe do an apache restart.
> 
sudo /etc/init.d/apache2 restart


---

