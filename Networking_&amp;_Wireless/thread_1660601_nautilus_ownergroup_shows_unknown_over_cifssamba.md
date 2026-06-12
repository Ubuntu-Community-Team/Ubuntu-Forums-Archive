---
title: "nautilus owner/group shows unknown over cifs/samba"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by gurpal2000 on 2011-01-05
Hi

I have a samba server running on meerkat like so:

```
[test]
comment = test folder
path = /test
public = no
writeable = yes
write list = @users
valid users = @users
force group = users
create mask = 644
force create mode = 0644
security mask = 0644
force security mode = 0644
directory mask = 0770
force directory mode = 0770
directory security mask = 0770
force directory security mode = 0770
```/test is owned by root:users with 755 which is fine.

Problem is when i mount the share on my other ubuntu desktop (same spec/os) using nautilus (Connect to Server) the Owner/Group columns show Unknown. Whereas if i navigate to the ~/.gvfs folder and browse inside the terminal it shows it as me (prob because smbfs mounts in my userspace).

What i really want is nautilus to show the true user on the server - that is i am expecting something like user1:users to be listed. I have configured both same users between server and client. Both use Ubuntu Meerkat 64. I've been following some of the share guides on [http://ubuntu.swerdna.org/ubusambaserver.html#shares](http://ubuntu.swerdna.org/ubusambaserver.html#shares) which are helpful. In windows 7 clients the Owner is correct but in Ubuntu, no.

Any pointers helpful

Thanks

---

### Post by slickvguy on 2011-04-03
I'm having the exact same problem. Did you find a solution?

Nothing to do with windows. All my samba, filesharing, printer sharing has been working fine for many months. I setup another ubuntu maverick box, and I now see that in nautilus on all my ubuntu boxes my shares' files show "unknown" in permissions, owner, and group. When you view the directory directly on the machine that they reside on, nautilus displays all the correct info. If you go into ~/.gvfs in the command box and do a ls -l, the permissions, owner, and group also display correctly. 

This is preventing copy/paste via nautilus for network shares, as well as things like importing bookmarks to FF from other machines, etc.

Any ideas?

---

