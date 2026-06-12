---
title: "system-config-samba"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by mosaic2s on 2011-10-26
Finally using samba with user specific folders and one comp as the file server.
The same comp also has citadel, efax running all the time. Its a great feeling to be using open source for office applications. And being able to manage with such lean sw utilities.

This comp has 2 hdd of 500mb each.
I am able to share and control the folders through system-config-samba utility. that is able to define the folders, users and it works ok.
But folders in the secondary hdd-that was earlier partitioned by windows - do not work that way. The system-config-samba utility works fine but on accessing the folder over network, an error comes.
[HTML]Unable to mount Location
Failed to mount Windows share[/HTML]

What am I missing here?

---

### Post by mosaic2s on 2011-10-29
moved the data from the secondary hdd and formatted it as ext3.
all sharing via samba config is working fine.

---

