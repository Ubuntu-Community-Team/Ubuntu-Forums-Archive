---
title: "Gwenview/DCOP error in Gnome"
date: 2006-11-10
forum: Multimedia &amp; Video
---

### Post by Shampyon on 2006-11-10
Tried to install Gwenview through Add/Remove. When I try to open a picture with it, I get these errors:

```
There was an error setting up interprocess communications in KDE. The message returned by the system was:

Could not read network connection list.
/home/MYUSERNAME/.DCOPserver_MYCOMPUTERNAME_0

Please check that the "dcopserver" program is running!

```

and

```
Could not find mime type
application/octet-stream
```

I'm using the default GNOME setup on Dapper.

---

### Post by Shampyon on 2006-11-12
Bumparumpadump for a two-day old question :-\"

---

### Post by Footissimo on 2006-11-24
Check your permissions on your .kde folder within your /home/user directory

---

### Post by tylerdurden on 2006-11-24
i am having the same problem... any other ideas?

---

### Post by Shampyon on 2006-11-25
> **Footissimo said:**
> Check your permissions on your .kde folder within your /home/user directory

This worked for me. Why do I always get caught by the simple things? :rolleyes:

---

### Post by Footissimo on 2006-11-26
..well it is a hidden directory!  Stumped me for ages too :)

Tyler - to be specific, check that the .kde directory (or any under it) aren't owned by root.

---

### Post by element on 2007-01-05
> **Footissimo said:**
> Check your permissions on your .kde folder within your /home/user directory

This worked for me as well. Thanks!

---

