---
title: "Fink Trouble"
date: 2007-01-26
forum: Mac OSX
---

### Post by Donnut on 2007-01-26
Hi.  Can anyone tell me how do edit the fink.conf file?  It is a read only file, testedit won't work, and apparaintly I do not have the required permissions.  I just wish to add the unstable repositories, but all web sites tell me to edit, no one tells me how!

---

### Post by Auria on 2007-01-26
There is no such thing as a read-only file, only files you don't have permission to write to ;)

you can just change the permissions of the file - graphically, it's "get info", "Permissions" (something like that - my system is in french), open little lock, change owner to be you, change all permissions to read and write

or the good old "sudo nano /sw/etc/fink.conf" will do it too

---

### Post by Donnut on 2007-01-27
Thanks, I just used sudo nano.  I had forgot about that.

---

