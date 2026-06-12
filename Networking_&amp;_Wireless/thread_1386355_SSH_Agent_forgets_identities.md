---
title: "SSH Agent forgets identities"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by HDave on 2010-01-20
This worked fine in 9.04, but doesn't in 9.10 (fresh install).

If I tell my ssh-agent about a private encrypted key via "ssh-add .ssh/mykey" then everything works fine.

But if I log out and then log back in it's not there and there is no Gnome prompt to ask for the password to decrypt.  So I have to do an "ssh-add" everytime I log in.  

Any ideas?

---

### Post by HDave on 2010-01-20
I think the problem is with seahorse.  I cannot import my key into seahorse as it complains "invalid file format".  The same key can be imported into seahorse under 9.04.

---

### Post by Brandon Williams on 2010-01-20
[This bug report](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/375341) might be related. It says that this problem existed in 9.04, too, which seems to rule it out. It's probably worth looking at though. Also, [here](http://ubuntuforums.org/showthread.php?t=1145017) is a related forum thread ... still about 9.04.

---

### Post by HDave on 2010-01-20
Noticed that Seahorse was behaving oddly in that it wouldn't let me delete my ssh key and had it in the wrong category.  Then I found this bug:

[https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/480034](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/480034)

which says that seahorse can corrupt the .gnupg datafiles.  Indeed that is what happened here.

A quick "mv .gnupg .gnupg.bak" and another ssh-add and everything was back to normal.

---

### Post by Lars Noodén on 2010-01-21
The tool you may be thinking of is [keychain](http://ubuntuforums.org/showpost.php?p=8699966&postcount=5).   When you log in, ubuntu runs ssh-agent for you and then when you log out, it kills the process.  To keep the keys active between sessions, use keychain.

---

