---
title: "Help separating frontend and backend."
date: 2011-05-15
forum: Mythbuntu
---

### Post by digitaldoug on 2011-05-15
I do a fresh install of Mythbuntu 11.04 64-bit as primary backend and frontend.  I am able to get it set up to watch live tv and to record and to download the guide info from SchedulesDirect.  But I cannot figure out how to get a frontend on a different computer working.  I can't even get the local frontend to work after changing the two IP address fields on the first page of the Host Address Backend Setup from 127.0.0.1 to the real IP address of the primary backend and changing the frontend General Setup Hostname from localhost to the real IP address.  After clicking Finish on the local frontend General Setup I get "Could not connect to the master backend server?  Is it running?  Is the IP address set for it in mythtv-setup correct?".  After reboot I get this goofy Country Language screen.  After "Save" I get "No UPnP".  After OK I get "Database Configuration 1/2".  "MythTV could not connect to the database.  Please verify your database settings below..."

I read something about enabling remote access to sql.  I tried modifying /usr/lib/mythtv/sql/mc.sql to replace localhost with "%".  Still no luck.

What am I missing?

---

### Post by Dan_R on 2011-05-15
You would want your local frontend to stay with localhost, your remote frontend should get the IP addresses of the master. Also make sure you have the correct password.

To enable remote MySQL access, just go into Mythbuntu Control Centre > MySQL and change it to Enable. Once that is done you should be able to connect.

---

### Post by laffinet on 2011-05-16
> **Dan_R said:**
> You would want your local frontend to stay with localhost

No you don't. The local frontend needs to have the proper IP address as well.

Do you use DHCP or static IP ? You need a static IP so your router doesn't keep changing the IP address of your backend.

---

### Post by uteck on 2011-05-16
Doesn't the Mythbuntu Control Centre handle setting these things up?  Just curious as that might be easier to use since the database on the backend also needs to be configured to allow external connections.

---

### Post by mbappe on 2011-05-16
Enabling remote SQL access in the MySQL section of Myth Control Centre was the ticket.  I don't know why it was not being enabled by default for a Primary Backend-only install.  Making that change and entering my user account password was all I needed to get up and running.  Thanks!

I posted the original request as digitaldoug.  I wasn't sure I had an account of my own at the time.  Now I'm logged in as me.

---

### Post by tgm4883 on 2011-05-16
> **mbappe said:**
> Enabling remote SQL access in the MySQL section of Myth Control Centre was the ticket.  I don't know why it was not being enabled by default for a Primary Backend-only install.  Making that change and entering my user account password was all I needed to get up and running.  Thanks!

I posted the original request as digitaldoug.  I wasn't sure I had an account of my own at the time.  Now I'm logged in as me.

Good point. Reported [https://bugs.launchpad.net/mythbuntu/+bug/783775](https://bugs.launchpad.net/mythbuntu/+bug/783775)

---

### Post by Lester_Burnham on 2012-05-20
Hi,

I'm also finding with Mythbuntu 11.10 and mythtv 0.25 from the mythbuntu PPA, that after doing an update, the external access to MYSQL has been disabled again.

This is really annoying, as i've fiddled with things on remote frontends that worked ok, a few times now, before remembering to check the external acccess for MYSQL which has been reset after updates.

This should be left alone.

Lester

---

