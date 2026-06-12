---
title: "Is this tunnelling possible?"
date: 2010-10-01
forum: Networking &amp; Wireless
---

### Post by dupa on 2010-10-01
I am logged in computer A.

Using a Citrix client, I open a "remote desktop" on a remote computer B (located in the client intranet).

I need to go to this remote desktop in order to browse on a website accessible only from the client Intranet.

My wish is to browse directly on that websites from my computer A.

the "only thing" I can do from computer B is to connect to "Internet" on websites (obviously only on port 80)

Is there someway to open a "reverse tunnel" this way:

When computer B connects to server C on port 80, it opens a port "locally" (the other endpoint of the TCP connection)

is possible to use this TCP socket to tunnel something?

---

### Post by jago25_98 on 2010-10-01
you need to specify what service the server is running. If it has ssh then yes it's possible with ssh.

i think you can also bounce ports with netcat... or something like that anyway...

---

### Post by dupa on 2010-10-13
I can have total control on "server C" so i can install ssh or anything I wish..

but from computer B I can only "go out" with HTTP through a corporate proxy.

---

### Post by jago25_98 on 2010-10-13
tunnelling may not be nessessary. In putty, for example there is an option to connect through the corp proxy. Most businesses have this set to allow because otherwise it can create unforeseen problems for admin who need to be able to ssh various places

give it a go

---

