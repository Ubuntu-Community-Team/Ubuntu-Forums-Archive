---
title: "ebox desktop with roaming profiles?"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by rozbuntu on 2009-10-06
Hi There,

I'm building a client/server network with ubuntu-server (including ebox software) and ubuntu-desktop (including the new package ebox-desktop).

Now for the problem.

When ebox-desktop is used, the user who logs in from the network gets a user directory created at /home/samba/users/<username> <-- this ain't really handy because when you log into another desktop you get a new profile. I would like the profiles to be synced so that the user can use one profile.

Now i tried to make a mounting point @ /home/samba/users and that actually works quite good, it writes away the profile data to the netwerk mount, but there's a problem there because it can't seem to write the gnome enviroment data to the mounted location. Does anyone have any idea to solve this problem so that we can use roaming profiles for the desktop pc's??

I hope i described the problem cleary, if this isn't the case please let me know and i'll try to explain it a bit better.

Thanx in advance,
-- rozbuntu

---

### Post by Dzingis on 2009-10-12
What happens if you enable the roaming profiles in Ebox File service (sharing or something else) menu? 

I'm also trying to setup something like you and I think it would be a good idea to help each other.

---

