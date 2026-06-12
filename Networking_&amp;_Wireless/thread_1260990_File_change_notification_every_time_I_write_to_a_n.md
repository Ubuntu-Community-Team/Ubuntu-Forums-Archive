---
title: "File change notification every time I write to a network drive"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by tatacalu on 2009-09-08
Hello!

I have a relatively common problem, but I don't seem to identify it's source.
I have a SAMBA server on my LAN to which there are mapped a few shares as network drives in windows xp (as Y:) and mounted as CIFS in linux [as /y].

The problem is that every time I save a file [either windows xp or linux] on the mapped drive / mounted folder, our IDEs alert us that the file changes right after the save.

I am running SAMBA 3.3.2.

Does anyone please have any idea ?

---

### Post by tatacalu on 2009-09-17
I found out what the problem was. The clocks of the 2 systems were out of sync. It turns out that the ntpd service wasn't enabled on neither systems.
[considering both the client and server running Linux - Fedora 11]

I synchronised the clocks, enabled and started the ntpd service and the problem seems to be fixed.

---

