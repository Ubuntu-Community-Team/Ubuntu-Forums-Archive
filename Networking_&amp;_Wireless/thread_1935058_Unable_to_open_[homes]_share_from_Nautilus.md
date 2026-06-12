---
title: "Unable to open [homes] share from Nautilus"
date: 2012-03-03
forum: Networking &amp; Wireless
---

### Post by axe87 on 2012-03-03
I have a number of shares set up on a Samba server including shared homes.

On my client ubuntu (11.10) machine Nautilus lists the various shares. I can click on all of them and access them, except the 'homes'.

The error I get is "Unable to mount location, Failed to mount Windows share"

Connecting to 'homes' works from the File -> Connect To Server menu option. Also, I can connect using smbclient from the command line. Therefore this looks like a Nautilus problem. I've seen a few threads on Nautilus share problems, but not this particular one.

---

### Post by Morbius1 on 2012-03-03
If you are talking about the [homes] share, one does not usually browse to and connect to a [homes] share because it is not created until asked for and is not by default browseable.

A Windows client automatically passes the login user's username and password when it browses the network so the [homes] share works seamlessly. 

A Linux client does not do that so it must be asked for explicitly by name:
```
nautilus smb://server-name/user-name
```

---

### Post by axe87 on 2012-03-04
Morbius1, thanks, I had a suspicion it was something like that. May be it was obvious but I couldn't see this mentioned anywhere.

---

