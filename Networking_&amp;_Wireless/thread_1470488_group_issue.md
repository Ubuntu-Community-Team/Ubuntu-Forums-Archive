---
title: "group issue"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by terbor on 2010-05-02
I am trying to be able to set a permanent ssh connection on the lan.  one other ubuntu desktop to mine.

I am getting this error.

> Could not chdir to home directory /home/robert/Public: Permission denied /usr/bin/X11/xauth:  timeout in locking authority file /home/robert/Public/.Xauthority -bash: /home/robert/Public/.bash_profile: Permission denied


From ls -l
```
drwxrwxrwx  6 robert fileshare  4096 2010-05-02 19:51 Public
```

From /etc/passwd
```
localPub:x:1001:1001:localPub:/home/robert/Public:/bin/bash
```

From /etc/group
```
localPub:x:1001:
fileshare:x:1002:localPub
```

Thanks for any help.

---

### Post by quixote on 2010-05-04
I'm not at all familiar with the fine points of ssh, but one thing that occurs to me is that you should check whether it's okay to have "rwxrwxrwx" (777) permissions on a directory.  I seem to remember that wide open permissions like that are rejected by default for security reasons.  (After all, why have ssh on a world-writable dir? ;))

---

