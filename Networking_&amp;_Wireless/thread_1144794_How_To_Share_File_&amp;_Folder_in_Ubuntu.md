---
title: "How To Share File &amp; Folder in Ubuntu"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by DeadGoat on 2009-05-01
Hi all...
i'm very new in the linux world...
now i got problem to share my folder with others in my network...
in the meantime i just manage to share my folder only in home folder, but when i'm trying to share other folders that located in different partition other that linux partition the error msg popup 

```
"'net usershare' returned error 255: net usershare add: cannot share path /media/Suck-On-This!/Video[s]/Anime as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = false" 
	to the [global] section of the smb.conf to allow this."
```

[IMG]http://www.sendspace.com/file/3zt6a1[/IMG]
[http://www.sendspace.com/file/3zt6a1](http://www.sendspace.com/file/3zt6a1)

so... what can i do to enable this?

---

### Post by coutts99 on 2009-05-01
"add the line "usershare owner only = false" to the [global] section of the smb.conf to allow this"

Have you tried doing what it tells you too?

---

### Post by DeadGoat on 2009-05-01
tried that also, but nothings change :confused:

---

### Post by DeadGoat on 2009-05-02
B u m p :(

---

