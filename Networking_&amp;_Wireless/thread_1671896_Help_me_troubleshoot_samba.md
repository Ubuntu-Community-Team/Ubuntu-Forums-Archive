---
title: "Help me troubleshoot samba"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by David_UK on 2011-01-20
Hi

I have 3 pc's on home network.  All dual boot Windows and Ubuntu.  All have Samba installed, plus personal file sharing.

When all 3 are booted into linux, all 3 show the public folders on all 3 pc's, but only 2 can access the other pc's folders.

I can't find any difference between the systems to explain why one pc (10.04) cannot mount either of the other two public folders: 

*Unable to mount location.  DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus) *

even though their icons are shown in 'network'.

The public folder on the troublesome pc can be accessed from the other two (10.04 & 10.10).

Any suggestions gratefully received.  Thanks

---

### Post by luvshines on 2011-01-23
Have you tried accessing the shares from command line of troublesome PC ?```

# List the shares
smbclient -L <other-server-ip> -U<username>%<passwd>

# Access any share
smbclient //<other-server-ip>/<share-name> -U<username>%<passwd>

```

Also might want to check firewalls on that PC

---

### Post by David_UK on 2011-01-23
Thank you.  I'm sorry this is a duplicate of the original thread - there were problems with the server when I posted.  I'll close this.

---

