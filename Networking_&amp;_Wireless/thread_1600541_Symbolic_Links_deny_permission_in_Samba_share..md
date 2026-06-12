---
title: "Symbolic Links deny permission in Samba share."
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by Jonny87 on 2010-10-19
I have a Samba share that contains a symbolic link and when I try accessing it from the WinXP machine it denies permission. If I access it from the Linux account, it goes in with no problems. Is there a certain setting that needs to be set or enabled or is this just one of those things with Samba?

---

### Post by Morbius1 on 2010-10-19
Samba has changed the ability to follow symlinks because of a security issue: [http://www.samba.org/samba/news/symlink_attack.html](http://www.samba.org/samba/news/symlink_attack.html)

To circumvent the change you could try this:

Add the following lines to the [global] section of smb.conf:
```
follow symlinks = yes
wide links = yes
unix extensions = no

```Then restart the samba service:
```
sudo service smbd restart
```

---

### Post by Jonny87 on 2010-10-19
> **Morbius1 said:**
> Samba has changed the ability to follow symlinks because of a security issue: [http://www.samba.org/samba/news/symlink_attack.html](http://www.samba.org/samba/news/symlink_attack.html)

To circumvent the change you could try this:

Add the following lines to the [global] section of smb.conf:
```
follow symlinks = yes
wide links = yes
unix extensions = no

```Then restart the samba service:
```
sudo service smbd restart
```

Ok thanks I'll give it a go.

---

### Post by jeremycobert on 2011-02-02
follow symlinks = yes
wide links = yes
unix extensions = no

that fixed the same issue for me , thanks !

---

### Post by Jonny87 on 2011-02-03
Sorry kinda forgot to get back to this thread. It also worked for me thanks.

I'll mark this as solved.

---

### Post by alhaines on 2011-09-05
Thanks! Worked for me.:P

---

