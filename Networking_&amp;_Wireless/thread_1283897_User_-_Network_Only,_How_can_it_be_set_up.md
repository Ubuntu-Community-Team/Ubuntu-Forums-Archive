---
title: "User - Network Only, How can it be set up?"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by Ordes on 2009-10-06
hi... i want to create a "backup" user on my second "server" pc (ubu 9.04, connecting by ssh,)

i was wondering if i can set the priviliges of "backup"

A) backup can only connect to the local network, so also share files only through local network, and cannot connect through the internet

--or--

B) to setup ssh that it only allows connection of my local ip from main pc (e.g 192.x)

what i basiclly try to enforce is, that all those "backup" folders can only be accessed through the network, and are cut off from internet.


thanks for any help

---

### Post by utnubuuser on 2009-10-06
can you make a new folder on your server. then lock the folder?  I don't know entirely how to, but I'm quite sure you can put a folder on the server so it would in the very least require a password to access. Maybe set the permissions to rwx------ (owner has read-write-execute permissions, group and others none)

---

### Post by Ordes on 2009-10-06
i was also thinking about making an encrypted container e.g truecrypt... the only problem i see here is the resizing of the container...

but yes.. just locking it up with an extra password might be a possibility.
;)

---

