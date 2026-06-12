---
title: "Is it possible to move /home folder to Ubuntu Server w/ Samba as PDC and use that"
date: 2012-07-07
forum: Networking &amp; Wireless
---

### Post by grunge09 on 2012-07-07
I have a Ubuntu 12.04 Server with Samba and win clients use the home folders fine.  I can't seem to get ubuntu clients to authenticate to the 12.04 Samba PDC Server properly.

I was wondering if I create a share on the server with my name, rsync my /home folder off the local machine to the server to that share name, then rename the local home folder and modify /etc/fstab to map the /home off the samba pdc share will that work.

I really do not want to install zentyl or Ldap.  Its just a small network.

Has anyone tried this?

---

### Post by Kirk Schnable on 2012-07-11
I see no reason why your home folder couldn't be a mounted Samba share.  I've done home folders that were symlinks before, it's not very picky.

There are a number of factors which make your decision questionable:
- Speed of home folder will be decreased by having it mounted remotely.
- If the network doesn't work or the server is down, your home folder is empty.
- Possibility of Samba misconfiguration resulting in your files being accessible to everyone on your network.

But I do believe what you're asking for is possible.

My coworker had Samba authentication with our Active Directory network working, for our My Documents redirect from the Windows system, but we never ended up implementing it.

---

