---
title: "how to network 3 9.04 ubuntu computers"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by iochinome on 2009-05-20
hey guys, so i need to set up three desktop computers all running 9.04 ubuntu so they all have a shared /home directory- i do not know where to start, though. they are all connected to the internet via ethernet cable and are up-to-date software wise. how would one go about this? thanks, help is much appreciated!

---

### Post by Iowan on 2009-05-20
If you're talking about a single shared /home directory somewhere, you may be looking for [LDAP]("https://help.ubuntu.com/community/OpenLDAPServer"). If you're talking about a /home directory on each machine (3 different directories) that the user can access, that might be accomplished a few different ways - NFS and SSHFS come to mind.

---

